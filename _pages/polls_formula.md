---
title: "Formel des Umfragemodells"
permalink: /polls/formula
author_profile: true
---


C: categories T: Time I: Institute

State Equation: $\theta_{c,t} \sim Normal(\theta_{c,t-1}, \epsilon_{c,t}); \ \ \theta_{c,0} \sim Normal(0,1); \ \ \epsilon_{c,t} \sim Normal(0,\sigma_{c}^\epsilon); \ c > 1$

Linear Predictor: $\lambda_{i,c,t} \sim \theta_{c,t}; \ c > 1$

Link Function: $\mu_{i,c,t} = \frac{exp(\lambda_{i,c,t})}{\sum_{a=1}^C exp(\lambda_{i,a,t})}; \ c > 1 \\ \mu_{i,1,t} = \frac{1}{\sum_{a=1}^C exp(\lambda_{i,a,t})}$

Measurement Equation I: $y_{i,c,t}^* \sim Dirichlet(\mu_{i,c,t}, \phi_{i}); \ \ \phi_i \sim Gamma(0.1, 0.1)$

Measurement Equation II: $y_{i,c,t} \sim Normal(y_{i,c,t}^*, \tau_{i,c,t})$

## Random Intercept

State Equation: $\theta_{c,t} \sim Normal(\theta_{c,t-1}, \epsilon_{c,t}); \ \ \theta_{c,0} \sim Normal(0,1); \ \ \epsilon_{c,t} \sim Normal(0,\sigma_{c}^\epsilon); \ c > 1$

Linear Predictor: $\lambda_{i,c,t} \sim \theta_{c,t}; \ c > 1$

Link Function: $\mu_{i,c,t} = \frac{exp(\lambda_{i,c,t})}{\sum_{a=1}^C exp(\lambda_{i,a,t})}; \ c > 1 \\ \mu_{i,1,t} = \frac{1}{\sum_{a=1}^C exp(\lambda_{i,a,t})}$

Measurement Equation I: $y_{i,c,t}^* \sim Dirichlet(\mu_{i,c,t}, \phi_{i}); \ \ \phi_i \sim e^{(\psi, \tau)}; \ \ \psi \sim Normal(0,100); \ \  \tau \sim Cauchy(0,5)$

Measurement Equation II: $y_{i,c,t} \sim Normal(y_{i,c,t}^*, \tau_{i,c,t})$
