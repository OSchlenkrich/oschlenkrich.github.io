---
title: "Umfragemodell"
permalink: /polls/
author_profile: true
---

Ich habe ein Umfragemodell für die Bundes- und Landtagswahlen entwickelt, das die Ergebnisse der unterschiedlichen Umfrageinstitute (Allensbach, Kantar/Emid, Forsa, Forschungsgruppe Wahlen, GMS, Infratest dimap, INSA und Yougov) bündelt. Die Daten stammen dabei von [wahlrecht.de](https://www.wahlrecht.de). 
Dieses Modell versucht den besten Wert zu eruieren, der sich für eine Partei ergibt. Dabei werden folgende Tatsachen durch die [Formel]({{ site.baseurl }}{% link _pages/polls_formula.md %}) berücksichtigt:
1. *Die Umfragewerte hängen zeitlich zusammen*: Von einem Zeitpunkt zum nächsten sind größere Umschwünge nicht wahrscheinlich, vielmehr ähneln sich zeitlich nahe beianander liegende Umfrageergebnisse. So wurde ein starker Zuwachs der Grünen von 23% auf 28% sowie ein starker Abfall der CDU/CSU von 28% auf 21% von Forsa am 20.04.2021 gemessen. Nach meinem Modell ist dieser starke Anstieg bzw. Abfall nicht realistisch, da das Modell gelernt hat, dass solche Umschwünge in der Zeitreihe nicht vorkommen. Dehsalb begrenzt das Modell den Anstieg bzw. den Abfall der Parteien in den Umfragewerten. 
2. *Kein Umfrageinstitut ist das beste*: Anstatt nur ein Umfrageinstitut einzubeziehen, ist es sinnvoll mehrere zu bündeln. Dadurch kann der Messfehler einzelner Institute ausgeglichen werden.
3. *Jede Umfragen ist an sich mit einem Messfehler behaftet*: Der Messfehler ist geringer, je größer die Stichprobe.   


Für die Bundestagswahl ergeben sich folgende Umfragewerte:


<iframe src="/plots/polls.html" height="600px" width="100%" style="border:none;"></iframe>

