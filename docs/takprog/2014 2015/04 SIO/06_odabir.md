﻿# Одабир
Аутор: 
Текст и тест примери: 
Анализа решења: Александар Вишњић
Тестирање: 

### Први подзадатак:
Задатак решавамо грубом силом: пролазимо по сваком $X$ од $L$ до $R$ и рачунамо префиксни минимум и максимум. Сложеност је $O(N\cdot Q)$.

### Други и трећи подзадатак:
Задатак решавамо **offline**, тј. прво учитамо све упите, сортирамо их по $L$ вредности, а затим пролазимо кроз низ $T$ од краја ка почетку. Док то радимо, памтимо низ $pos_i$ који нам говори информацију о првом следећем индексу појављивања члана $i$ у низу $T$. Тај низ има величину $1000$, јер је то максимална вредност $T_i$ у овом подзадатку. Сада за сваки упит знамо интересантне позиције: Потребно је само по њима проћи и израчунати збир максимума и минимума. Сложеност овог алгоритма је $O(Q\cdot maxT_i \cdot logN)$ или $O(Q\cdot maxT_i)$ у зависности од имплементације.

### Главно решење:
Слично као раније, задатак решавамо **offline**. Када идемо од краја ка почетку, потребно је одржавати и лењо сегментно стабло над низом $T$. Њиме памтимо максимум на сегменту, а ажурирамо га тако што додајемо (или одузимамо) одређен број на распону. Оно нам говори информацију о решењу задатка за свако $X$ између $L$ и $N$. 

Прецизније, интересантних позиција сада има много и није могуће увек проћи по њима за сваки упит. Зато памтимо два **stack-а** парова који нам говоре информације о следећем мањем/већем елементу у низу $T$. Када вршимо упите распона на нашем сегментном стаблу, бришемо елемент из једног од *stack*-ова. То значи да укупна сложеност остаје $O(N+QlogN)$, Пошто у наше *stack*-ове додајемо највише један елемент по проласку кроз низ $T$, а не можемо обрисати више него што смо додали.
