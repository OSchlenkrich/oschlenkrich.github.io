---
title: "Formel des Umfragemodells"
permalink: /polls/formula/
author_profile: true
---

Das Umfragemodell basiert auf einem sogenannten *state space model*. Dieses state space model erlaubt, dass die Werte zum einen zeitlich voneinander abhängen können und dass zum anderen geht es davon aus, dass die Umfragewerte nur mit einem Messfehler gemessen werden können. Das erste Merkmale wird in der *state equation* formuliert, während das zweite Merkmal in der *measurement equation* modelliert wird. In der state equation wird für die Umfrageegebnisse der einzelnen Parteien eine latente Variable ($\theta_{c,t}$) eingesetzt, die so modelliert wird, dass sie zu einem gewissen Grad von den vergangenen Werten abhängt ($\theta_{c,t-1}$). Die Werte der latenten Variable sind daher autoregressive miteinander verbunden.

In der measurement equation werden zwei Arten von Messfehlern berücksichtigt: Zum einen wird für jedes Umfrageinstitut ein Zuverlässigkeitswert ($\phi_{i}$) berechnet. Es wird davon ausgegangen, dass manche Institute besser als andere bei der Vorhersage der Werte sind. Da die Zuverlässigkeit von Instituten, bei denen anfangs nur wenige Datenpunkte vorhanden sind, nicht präzise geschätzt werden kann, erhalten diese erstmal einen Wert, der Nahe dem Durchschnitt der Zuverlässigkeit aller Institute liegt ($\beta$) Je mehr Datenpunkte jedoch für ein Institut vorhanden sind, desto präziser kann dieser Wert geschätzt werden und desto stärker kann der Wert vom Mittelwert abweichen.

Zum anderen wird davon ausgegangen, dass größere Stichproben zuverlässiger sind als kleinere Stichproben. Daher wird für jede Partei und Stichprobe ein Zuverläsigkeitswert ($\tau_{i,c,t}$) berechnet. Dieser ergibt sich nach der folgenden Formel: ($\sqrt{\frac{(1-p)*p}{n}}$) , wobei *p* das Umfrageerbenisse für die Partei ist und *n* die Stichprobengröße.

In Kontrast zu anderen Umfragemodellen basiert dieses Modell nicht nur auf der Normalverteilung sondern vor allem auf der [Dirichlet-Verteilung](https://de.wikipedia.org/wiki/Dirichlet-Verteilung). Die Dirichlet-Verteilung erlaubt es, die Daten so zu modellieren, dass alle Werte der Parteien immer auf 100% summieren. So ergeben sich immer valide Ergebnisse.

Die Gesamtformel sieht so aus:

*C: categories T: Time I: Institute*

*State Equation*: $$\theta_{c,t} \sim Normal(\theta_{c,t-1}, \epsilon_{c,t}); \ \ \theta_{c,0} \sim Normal(0,1); \ \ \epsilon_{c,t} \sim Normal(0,1); \ c > 1$$

*Linear Predictor*:

$$\lambda_{i,c,t} \sim \theta_{c,t}; \ c > 1$$

*Link Function*:

$$\mu_{i,c,t} = \frac{exp(\lambda_{i,c,t})}{\sum_{a=1}^C exp(\lambda_{i,a,t})}; \ c > 1 \\ \mu_{i,1,t} = \frac{1}{\sum_{a=1}^C exp(\lambda_{i,a,t})}$$

*Measurement Equation I*:\
$$y_{i,c,t}^* \sim Dirichlet(\mu_{i,c,t}, e^{\phi_{i}});$$

*Measurement Equation II*:

$$y_{i,c,t} \sim Normal(y_{i,c,t}^*, \tau_{i,c,t})$$

*Random Intercept für* $\phi_{i}$:

$$phi_i \sim Normal(\beta, \pi)$$

$$\beta \sim Normal(3,1)$$

$$\pi \sim Normal(0,0.2)$$
