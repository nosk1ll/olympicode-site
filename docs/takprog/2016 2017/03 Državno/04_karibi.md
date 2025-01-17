﻿
# Кариби

Аутор: 
Текст и тест примери: 
Анализа решења: 
Тестирање:

Број $A_{i,j}$ је једнак $1$ ако је на пољу $(i,j)$ у заливу копно, а иначе $0$.

### Решење за $1 \leq N,M \leq 80$:
Можемо за свако паркинг место Џековог брода дужине $a$ споро рачунати број паркинг места за Барбосин брод дужине $b$ у том случају, користећи префискне суме појединачних колона и врста матрице $A$. Временска сложеност: $O(N^2M^2)$, меморијска сложеност: $O(NM)$.

### Решење за $N=1$ и $1 \leq M \leq 2000$:
За овај подзадатак довољно је решење изложено у претходном, али је њега овде могуће лакше имплементирати зато што је $N=1$. Временска сложеност: $O(M^2)$, меморијска сложеност: $O(M^2)$.

### Решење за $a=1$ и $1 \leq N,M \leq 2000$:
Нека је $D_{i,j}^{b}$ једнако $1$ ако је $i+b-1 \leq N$ и $\sum_{k=i}^{i+b-1} A_{k,j} = 0$ (тј. ако су сва поља колоне $j$ од $(i,j)$ до $(i+b-1,j)$ под водом), а $0$ иначе. Слично дефинишемо  и $R_{i,j}^{b}$ за поља $(i,j)$ и $(i,j+b-1)$. Аналогно, могу бити корисне и вредности $D_{i,j}^{a}$ и $R_{i,j}^{a}$ које рачунамо на исти начин, само за брод дужине $a$. Ови подаци нам омогућују да проверимо да ли је могуће упаркирати брод дужине $b$ или $a$ у неко место, а можемо их лако пронаћи помоћу префиксних сума појединачних колона и врста матрице $A$. 

Сада можемо да израчунамо број $C_0$ - на колико начина је могуће паркирати брод дужине $b$ у заливу: $$C_0=\sum_{i=1}^{N} \sum_{j=1}^{M} D_{i,j}^{b}+R_{i,j}^{b}$$ 

Покушаћемо да брод дужине $a$ паркирамо са почетком у сваком пољу $(i,j)$ редом, и да израчунамо колико смо при томе блокирали места за паркирање броду дужине $b$. 

На пример, вертикалним паркирањем брода дужине $a$ од поља $(p,q)$ до поља $(p+a-1,q)$ (где је $p+a-1 \leq N$) блокирали смо тачно $$V_{i,j}=(\sum_{i=p}^{p+a-1} \sum_{j=q-b+1}^{q} R_{i,j}^{b}) + (\sum_{i=p-b+1}^{p+a-1} D_{i,q}^{b})$$ паркинг места за брод дужине $b$. При том се подразумева да ако је нека од граница у овим сумама мања од $1$, суму ћемо почети од $1$, односно ако је већа од индекса највеће колоне или врсте ($N$ или $M$ у зависности од тога да ли се ради о граници за $i$ или $j$), суму ћемо завршити на одговарајућем постојећем индексу. Ова формула важи јер смо у ствари оваквим паркирањем брода дужине $a$, заузели сва места за брод дужине $b$ чији се леви крајеви налазе у подматрици са горњим левим пољем $(p,q-b+1)$ и доњим десним пољем $(p+a-1,q)$, као и сва места чији су горњи крајеви поља у $q$-тој колони од $(p-b+1,q)$ до $(p+a-1,q)$.

На сличан начин можемо пронаћи израз за број блокираних поља при хоризонталном паркирању брода дужине $a$ од поља $(p,q)$ до поља $(p,q+a-1)$ (где је $q+a-1 \leq M$): 
$$H_{i,j}=(\sum_{i=p-b+1}^{p} \sum_{j=q}^{q+a-1} D_{i,j}^{b}) + (\sum_{j=q-b+1}^{q+a-1} R_{p,j}^{b})$$

У овом случају, паркинг места која заузимамо су она са горњим крајевима у подматрици са горњим левим пољем $(p-b+1,q)$ и доњим десним пољем $(p,q+a-1)$, као и паркинг места чији су леви крајеви у $p$-тој  врсти од поља $(p,q-b+1)$ до поља $(p,q+a-1)$.

У овом подзадатку првe сумe у изразима за $V_{i,j}$ и $H_{i,j}$ се знатно поједностављују јер је $a=1$, па је могуће користити стандардне префиксне суме сваке колоне и сваке врсте матрица $R_{i,j}^{b}$ и $D_{i,j}^{b}$ за рачунање вредности $V_{i,j}$ и $H_{i,j}$.

Најмањи број начина за паркирање Барбосиног брода који Џек Врабац може да постигне добијамо као минималну вредност коју узима $\min(C_0-V_{i,j},C_0-H_{i,j})$ по свим пољима $(i,j)$ у заливу. Временска сложеност: $O(NM)$, меморијска сложеност: $O(NM)$.

### Решење за: $1 \leq N,M \leq 500$:
У овом подзадатку је због мањих димензија матрице могуће рачунање $V_{i,j}$ и $H_{i,j}$ само уз помоћ префиксних сума врста и колона матрица $R_{i,j}^{b}$ и $D_{i,j}^{b}$. На пример, у првој суми у изразу за $V_{i,j}$ ћемо за сваку врсту од $p$ до $p+a-1$ користисти префиксну суму те врсте у матрици $R_{i,j}^{b}$ да израчунамо  $\sum_{j=q-b+1}^{q} R_{i,j}^{b}$. Другу суму у изразу за $V_{i,j}$ можемо и даље рачунати спорим сабирањем одговарајућих вредности $D_{i,j}^{b}$. Временска сложеност: $O(NM \cdot \max(N,M))$, меморијска сложеност: $O(NM)$.

### Главно решење:

За довољно брзо рачунање вредности $V_{i,j}$ и $H_{i,j}$ ће нам бити потребне дводимензионалне префиксне суме матрица $R_{i,j}^{b}$ и $D_{i,j}^{b}$. Дводимензионална префиксна сума произвољне матрице $X$ је матрица $Y$ истих димензија за коју за свако њено поље $(p,q)$ важи $Y_{p,q}=\sum_{i=1}^{i=p} \sum_{j=1}^{j=q} X_{i,j}$. Помоћу ње можемо у константном  времену израчунати суму бројева у било којој подматрици матрице $X$. На пример, суму бројева у подматрици матрице $X$ са горњим левим пољем $(p,q)$ и доњим десним пољем $(r,s)$ налазимо као: $$\sum_{i=p}^{i=r} \sum_{j=q}^{j=s} X_{i,j}=Y_{r,s}-Y_{p-1,s}-Y_{r,q-1}+Y_{p-1,q-1}$$

Ово нам омогућава да у константном времену нађемо вредности $V_{i,j}$ и $H_{i,j}$ за свако поље у заливу. Минимални број места који Џек може постићи као и пре добијамо као минималну вредност коју узима $\min(C_0-V_{i,j},C_0-H_{i,j})$ по свим пољима $(i,j)$.

Временска сложеност: $O(NM)$, меморијска сложеност: $O(NM)$.
