﻿# Анти жмурке
Аутор: 
Текст и тест примери: 
Анализа решења: Александар Вишњић
Тестирање: 

### Прва два подзадатка:
Трагач $i$ чини да неко поље $(x,y)$ има скривеност највише $\lceil\frac{|X_i-x|+|Y_i-y|}{V_i}\rceil$. Скривеност поља је минимална скривеност од свих трагача. Ако за свако поље то одредимо преко грубе силе имамо алгоритам сложености $O(N\cdot M\cdot K)$.

### Трећи подзадатак:
Потребно је брже проверити скривеност сваког поља. Пошто су брзине једнаке, то можемо урадити претрагом у ширини са извором у координатама сваког трагача. Израчунаћемо поље које има највећу удаљеност од сваког трагача и поделићемо је са константном брзином како бисмо добили скривеност. Сложеност је $O(N\cdot M)$.

### Главно решење:
Када брзине нису једнаке, можемо радити бинарну претрагу по решењу: потребно је проверити да ли је дату скривеност могуће постићи. Тачније, ако је скривеност $S$ могућа, за сваког трагача $i$ знамо да покрива сва поља на удаљености $S\cdot V_i$ и да након тога остаје бар једно слободно поље (и њега је потребно исписати за највећу скривеност). Ако не остаје слободно поље, тражена скривеност није могућа.  Проверу да ли оно постоји радимо претрагом у ширини, али не преко реда него преко низа вектора: за сваку "дубину" памтимо сва поља која се налазе на њој. Суседна поља која нису посећена у следећем кораку имају дубину за једну мању од тренутне. Најмања могућа дубина посећеног поља је $0$. Извори имају координате $(X_i,Y_i)$ и дубину $S\cdot V_i$.
