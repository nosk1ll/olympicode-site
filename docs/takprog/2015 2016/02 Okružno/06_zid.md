﻿
Аутор: 
Текст и тест примери: 
Анализа решења: Александар Вишњић
Тестирање: 
### Обзервација:
Ако једно теме правоугаоног зида има координате $(x,y)$, онда остала имају $(x,-y)$, $(-x,y)$ и $(-x,-y)$. Због симетрије, задатак можемо решавати само у првом квадранту: узећемо **апсолутну вредност** координата свих села, а зид ће покривати сва села у правоугаонику са теменима $(0,0)$, $(x,0)$, $(0,y)$ и $(x,y)$ и његова цена ће бити $4C\cdot (x+y)$. Село $i$ припада зиду акко $X_i\leq x$ и $Y_i\leq y$.

### Подзадатак 1:

У овом подзадатку можемо изградити сваки могући зид јер их има довољно мало и проверити за свако село да ли је у њему, и на основу тога да израчунамо цену изградње зида и освајања свих осталих.
Ако је $M=max(max|X_i|,max|Y_i|)$, зидова које проверавамо има највише $(M+1)^2$, а укупна сложеност је $O(M^2\cdot N)$.

### Подзадатак 2:
$X$ координате села се могу поређати у **сортиран** низ и потребно је изградити "префикс" чија цена линеарно зависи од његове дужине и на ту цену додати суфиксни максимум (најскупље село за освојити ван тог префикса)  који смо раније израчунали за свако село. Приметимо да је у овом случају оптимално градити зид са крајем у селу. Сложеност је $O(NlogN)$ или $O(N+M)$ због сортирања.

### Подзадатак 3:

Село са координатама $(X_i,Y_i)$ можемо разложити на два села са $(X_i,0)$ и $(0,Y_i)$. Није тешко видети да се оба "разложена" села морају освојити како се његова цена не би урачунала у максимум, самим тим је ово еквивалентан задатак. Сада имамо два  соритрана низа ("хоризонтална" и "вертикална" села). Градимо зид који има координате међу овим разложеним селима, њих има $O(N^2)$ и у цену освајања рачунамо суфиксне максимуме ова два низа за ефикасно решење.

### Подзадатак 4

Претпоставимо да плаћамо $Z$ златника за освајање села ван зида. Преостаје нам само да оградимо села са већом ценом. То можемо радити једним опадајућим проласком по свим вредностима $Z$ тако што након изградње зида за одређену вредност и након рачунања цене додамо сва села са том истом ценом у зид (како бисмо гарантовали да више не плаћамо за њих); ако је оно ван, онда једноставно променимо димензије зида најмање што можемо тако да оно буде унутар (другим речима, постављамо $x=max(x,X_i)$ и $y=max(y,Y_i)$). Користећи *counting sort* добијамо сложеност $O(N+max(W_i))$.
