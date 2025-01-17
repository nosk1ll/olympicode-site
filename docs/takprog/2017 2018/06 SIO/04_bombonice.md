﻿## Анализа

Лако се закључује да се при додавању бомбоница, оне додају у кутије $P, P+1, P+2, ..., P+K-1$. За нијансу је једноставнији случаја када је  $P+K-1\leq N$. Ако уведемо оѕнаку $R=P+K$, онда ће у кутију број $I$ ($P\leq I\leq P+K-1=R-1$) бити додато $(R-I)^2$ бомбоница, Ако узмемо у обзир да је $(R-I)^2 = R^2 - 2R\times I + I^2$, то број додатих куглица можемо баш посматрати као три засебна сабирка (који ће формирати током трајања три засебна збира). Да би ефикасно могли да ефикасно ажурирамо збирове (по појединачним кутијама) и ефикасно одређуејмо збирове блокова узастопних кутија, формирамо три сегментна стабла. Једно које збраја фиксни сабирак у операцији додавања ($R^2$), друго које броји колико смо пута садржај $I$-те кутије увећали за $I$ (у горњем примеру то је $-2R$) и треће које броји колико смо пута садржај $I$-те кутује увећали за $I^2$ (у горњем примеру то је $1$). Ако та сегемнтна стабла формирамо на тај начин, онда ћемо касније моћи ефикасно да пребројимо укупан број бомбоница у блоковима узастопних кутија. 

Ако је  $P+K-1> N$, онда додавање бомбоница раздвајамо у два додавања: у првом додавању је $P1=P$ $K1=N-P+1$, а у другом је $P2 = 1$ и $K2=K-K1$.

Слично се пребрајање бомбоница раздваја на два случаја. Ако је $X+T-1\leq N$, онда је довољан једно сабирање по сегментном стаблу за блок (интервал) $X,X+T-1]$. Ако је $X+T-1.>N$, онда су потребна два упита/збира: ѕа интервале $X, N]$ и $[1,T-(N+1-X)]$.
 


> Written with [StackEdit](https://stackedit.io/).