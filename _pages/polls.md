---
title: "Umfragemodell"
permalink: /polls/
author_profile: true
---

Dieses Umfragemodell bündelt die Ergebnisse der unterschiedlichen Umfrageinstitute (Allensbach, Kantar/Emid, Forsa, Forschungsgruppe Wahlen, GMS, Infratest dimap, INSA und Yougov) zur Sonntagsfrage. Die Daten stammen dabei von [en.wikipedia.org](https://en.wikipedia.org/wiki/Opinion_polling_for_the_2021_German_federal_election). Dabei sammelt wikipedia nicht nur die Umfrageergebnisse für die Bundestagswahl, sondern es finden sich auch die Ergebnisse für die Parlamentswahlen in anderen Ländern, so dass das Umfragemodell leicht auf andere Länder ausgedehnt werden kann.

Dieses Modell versucht den besten Wert zu eruieren, der sich für eine Partei ergibt. Dabei werden folgende Tatsachen in dem Modell berücksichtigt:

1\. *Die Umfragewerte hängen zeitlich zusammen*: Von einem Zeitpunkt zum nächsten sind größere Umschwünge nicht wahrscheinlich, vielmehr ähneln sich zeitlich nahe beianander liegende Umfrageergebnisse. So wurde ein starker Zuwachs der Grünen von 23% auf 28% sowie ein starker Abfall der CDU/CSU von 28% auf 21% von Forsa am 20.04.2021 gemessen. Nach meinem Modell ist dieser starke Anstieg bzw. Abfall nicht realistisch, da das Modell gelernt hat, dass solche Umschwünge in der Zeitreihe nicht vorkommen. Dehsalb begrenzt das Modell den Anstieg bzw. den Abfall der Parteien in den Umfragewerten.

2\. *Kein Umfrageinstitut ist das beste*: Anstatt nur ein Umfrageinstitut einzubeziehen, ist es sinnvoll mehrere zu bündeln. Dadurch kann der Messfehler einzelner Institute ausgeglichen werden.

3\. *Jede Umfragen ist an sich mit einem Messfehler behaftet*: Der Messfehler ist geringer, je größer die Stichprobe.

[Eine detailliertere Erklärung findet sich hier.]({% link _pages/polls/polls_formula.md %})


Für die Bundestagswahl ergeben sich folgende Umfragewerte für die einzelnen Parteien:

<iframe src="/plots/polls.html" height="600px" width="100%" style="border:none;">

</iframe>
