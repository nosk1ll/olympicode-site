# Име Задатка

Аутор: Павле Мартиновић
Текст и тест примери: Павле Мартиновић
Анализа решења: Павле Мартиновић
Тестирање: Алекса Милојевић

﻿### $N=1,Q\leq200$
Овај подзадатак је само најпростија симулација. Приметимо да је Мома у сваком тренутку освојио неки интервал и да су једина нова поља које може освојити она два на крајевима интервала. Сада у сваком тренутку видимо да ли је једно од та два суседна поља баш оно које нам треба и ако јесте освојимо га. Сложеност $O(QMN)$.
### $Q\leq200$
И овај подзадатак је обична симулација, али се мора генерализовати на дводимензионе табле. Памтићемо за свако $i$ да ли је поље означено са тим бројем суседно некоме од тренутно освојених поља. Онда, када то поље освојимо означићемо његове суседе као могуће за освајање. Тако, итерирајући по вредностима од $2$ до $MN$ можемо да утврдимо да ли је могуће да Мома испуни задатак. Сложеност $O(QMN)$.
### Пуно решење
Приметимо следећи потребан и довољан услов да Мома испуни задатак:
Нека кажемо да је поље *лоше* ако су му сви суседи означени са вредностима већим од његове вредности. Мома може да испуни свој задатак ако и само ако постоји тачно једно лоше поље.
Докажимо ово. Приметимо да је поље означено са бројем $1$ свакако лоше. Ако је могуће да Мома испуни задатак онда свако друго поље има неког суседа којег је Мома већ освојио у том тренутку - то јест. неког суседа са мањим индеском од њега, па је један смер доказан. У другом смеру, ако претпоставимо да свако поље са индексом $>1$ има суседа мањег индекса од њега, онда можемо лаком индукцијом да докажемо да Мома може да испуни свој циљ: по хипотези, Мома може да освоји првих $k$ поља, а поље са индексом $k+1$ има неког суседа са мањим индексом, то јест неко већ освојено поље, стога Мома може да настави освајање.
Сада кад смо доказали ово, потребно је у сваком тренутку пазити колико постоји лоших поља. На почетку пребројимо колико је лоших поља и приметимо да кад заменимо два поља, то може једино да промени "лошост"  највише $10$ поља: та два што смо заменили и њихових суседа. Онда напросто ажурирамо да ли су она постала лоша сад и испишемо "DA" уколико имамо само једно лоше поље и "NE" у супротном. Сложеност $O(NM+Q)$.
