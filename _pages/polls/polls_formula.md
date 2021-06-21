---
title: "Formel des Umfragemodells"
permalink: /polls/formula/
author_profile: true
---

Das Umfragemodell basiert auf einem sogenannten *state space model*. Dieses state space model geht zum einen davon aus, dass die Werte zum einen zeitlich voneinander abhängen können und dass zum anderen die Umfragewerte nur mit einem Messfehler gemessen werden können. Das erste Merkmale wird in der *state equation* formuliert, während das zweite Merkmal in der *measurement equation* modelliert wird. In der state equation wird für die Umfrageegebnisse der einzelnen Parteien eine latente Variable ($\theta_{c,t}$) eingesetzt, die so modelliert wird, dass sie zu einem gewissen Grad von den vergangenen Werten abhängt ($\theta_{c,t-1}$). Die Werte der latenten Variable sind daher autoregressiv miteinander verbunden.

In der measurement equation werden zwei Arten von Messfehlern berücksichtigt: Zum einen wird für jedes Umfrageinstitut ein Zuverlässigkeitswert ($\phi_{i}$) berechnet. Es wird davon ausgegangen, dass manche Institute besser als andere bei der Vorhersage der Werte sind. Da die Zuverlässigkeit von Instituten, bei denen anfangs nur wenige Datenpunkte vorhanden sind, nicht präzise geschätzt werden kann, erhalten diese erstmal einen Wert, der Nahe dem Durchschnitt der Zuverlässigkeit aller Institute liegt ($\beta$) Je mehr Datenpunkte jedoch für ein Institut vorhanden sind, desto präziser kann dieser Wert geschätzt werden und desto stärker kann der Wert vom Mittelwert abweichen.

Zum anderen wird davon ausgegangen, dass größere Stichproben zuverlässiger sind als kleinere Stichproben. Daher wird für jede Partei und Stichprobe auch ein Zuverlässigkeitswert ($\tau_{i,c,t}$) berechnet. Dieser ergibt sich nach der folgenden Formel ($\sqrt{\frac{(1-p)p}{n}}$), wobei *p* das Umfrageerbenisse für die Partei und *n* die Stichprobengröße sind.

In Kontrast zu anderen Umfragemodellen basiert dieses Modell nicht nur auf der Normalverteilung sondern vor allem auf der [Dirichlet-Verteilung](https://de.wikipedia.org/wiki/Dirichlet-Verteilung). Die Dirichlet-Verteilung erlaubt es, die Daten so zu modellieren, dass alle Werte der Parteien immer auf 100% summieren. So ergeben sich immer valide Ergebnisse.

Die Gesamtformel sieht so aus:

*C: categories T: Time I: Institute*

*State Equation*:

$$\theta_{c,t} \sim Normal(\theta_{c,t-1}, \epsilon_{c,t}); \ \ \theta_{c,0} \sim Normal(0,1); \ \ \epsilon_{c,t} \sim Normal(0,1); \ c > 1$$

*Linear Predictor*:

$$\lambda_{i,c,t} \sim \theta_{c,t}; \ c > 1$$

*Link Function*:

$$\mu_{i,c,t} = \frac{exp(\lambda_{i,c,t})}{\sum_{a=1}^C exp(\lambda_{i,a,t})}; \ c > 1 \\ \mu_{i,1,t} = \frac{1}{\sum_{a=1}^C exp(\lambda_{i,a,t})}$$

*Measurement Equation I*:

$$y_{i,c,t}^* \sim Dirichlet(\mu_{i,c,t}, e^{\phi_{i}})$$

*Measurement Equation II*:

$$y_{i,c,t} \sim Normal(y_{i,c,t}^*, \tau_{i,c,t})$$

*Random Intercept für* $\phi_{i}$:

$$phi_i \sim Normal(\beta, \pi)$$

$$\beta \sim Normal(3,1)$$

$$\pi \sim Normal(0,0.2)$$

Dies ergibt den folgenden [Stan-code](https://mc-stan.org/):


```
data {
  int<lower=0> N; // number of observations
  int<lower=0> Ti; // number of time points
  int<lower=0> C; // number of no. categories

  int<lower=0> T[N]; // time Index
  int<lower=0> id[N]; // polling institute index

  matrix[N,C] y; // poll results
  matrix[N,C] y_sd; // poll sd 
}

transformed data {
  int max_id;
  max_id = max(id);  // number of no.  polling institutes
}

parameters {
  vector<lower=0>[C-1] theta_sd; // sd state equation
  matrix[Ti, C-1] theta; // hidden state
 
  vector[max_id] phi_raw; // random effets for precision
  real phi_mu;
  real<lower=0> phi_sd;

  simplex[C] y_star[N]; // result measurement equation I 
}

transformed parameters{
  matrix[Ti, C] mu;
  vector[max_id] phi;
  
  phi = exp(phi_mu + phi_raw * phi_sd); // non-centered parametrization
  
  for (t in 1:Ti) {
    mu[t] = to_row_vector(softmax(to_vector(append_col(0, theta[t])))); 
  }
}

model {
 // priors
 theta_sd ~ normal(0, 1);
 phi_raw ~ std_normal();
 phi_sd ~ normal(0, 0.2);
 phi_mu ~ normal(3, 1);

 for (t in 1:Ti) {
   if (t == 1) {
     theta[1] ~ normal(0, 1);  
   } else  {
     theta[t] ~ normal(theta[t-1], theta_sd);
   }
 }
  
  // likelihood  
  for (i in 1:N) {
    y_star[i] ~ dirichlet(to_vector(mu[T[i]])*phi[id[i]]); 
    y[i] ~ normal(y_star[i], y_sd[i]);
  }
}

generated quantities {
  matrix[N,C] y_rep;

  for (i in 1:N) {
    for (c in 1:C) {
      y_rep[i,c] = normal_rng(y_star[i,c], y_sd[i,c]);
    }
  }
}
```


