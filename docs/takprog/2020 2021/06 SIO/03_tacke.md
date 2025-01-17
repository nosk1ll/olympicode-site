# Тачке

Аутор: Тадија Шебез
Текст и тест примери: Тадија Шебез
Анализа решења: Тадија Шебез
Тестирање: Алекса Милисављевић

Одговор на упит је `Da` ако се тачка $P$ налази у унутрашњости или на конвексном омотачу подниза тачака од $L$ до $R$ (са специјалним случајем када су све тачке колинеарне и конвексни омотач је заправо дуж или једна тачка).

### Решење када је $N, Q \leq 100$

За сваки упит можемо у $O(N^2)$ да нађемо конвексни омотач и проверимо да ли се тачка $P$ налази унутар или на омотачу. Временска сложеност је $O(QN^2)$.

### Решење када је $N, Q \leq 2500$

Решење је исто као за прошли подзадатак само што је потребан ефикаснији алгоритам за налажење конвексног омотача. Са алгоритмом у $O(NlogN)$ добијамо временску сложеност $O(QNlogN)$.

### Решење када је $N, Q \leq 10^5$ и све тачке су на X оси.

Конвексни омотач је заправо дуж на $X$ оси па су нам битне тачка са најмањом и тачка са највећом X координатом за сваки упит. Ако за проналажење минимума и максимума користимо сегментно стабло добијамо временску сложеност $O(QlogN)$.

### Решење када је $N, Q \leq 10^5$ и постоје две праве тако да се свака тачка из низа $A$ налази на бар једној од њих

Узмимо 3 различите тачке. Бар један од 3 пара ових тачака се сигурно налази на истој правој. Испробајмо сва три пара и проверимо да ли су све тачке које нису колинеарне са тренутним паром међусобно колинеарне. На овај начин ћемо наћи две праве које садрже све тачке из низа. За сваки упит битне су нам само екстремен тачке на овим правама и њих можемо брзо да нађемо за сваки упит уз помоћ сегментног стабла. На овај начин добијамо конвексни омотач са највише 4 тачке и једноставно можемо да проверимо да ли се тачка $P$ налази у њему. Временска сложеност овог алгоритма је $O(QlogN)$.

### Решење када је $N, Q \leq 6 \times 10^4$ и све координате су цели бројеви из интервала $[-500, 500]$

За скуп тачака са целобројним координатама у квадрату димензија $M \times M$ највећи број тачака на конвексном омотачу је око $M^{2/3}$. Решење за овај подзадатак је да чувамо конвексне омотаче у сваком чвору сегментног стабла и радимо њихова спајања. Временска сложеност је $O(QlogNM^{2/3})$. Ово решење такође пролази и све претходне подзадатке.

### Решење за 100 поена

За сако $i$ нађимо најмању границу $G_i$ тако да се тачка $P$ налази у конвексном омотачу подниза од $i$ до $G_i$. Ако не постоји такав подниз узећемо $G_i=N+1$. Приметимо да је низ $G_i$ неопадајући, па га можемо наћи применом **two pointers** технике. Потребна нам је још структура података која подржава операције убацивања и избацивања тачака и одговара на питање да ли је тачка $P$ унутар конвексног омотача. Посматрајмо случај када се тачка $P$ налази у конвексном омотачу неког скупа тачака. За сваку праву која пролази кроз $P$, постоје две тачке које су са различитих страна те праве, или постоји тачка која је на тој правој. Постматрајмо сада слчај када тачка $P$ није у конвексном омотачу неког скупа тачака. У овом случају постоји права која пролази кроз $P$ таква да су све тачке из скупа са једне њене стране. Посматрајмо тачке из овог скупа сортиране кружно по углу око $P$. Ако постоји права таква да су све тачке са једне њене стране постоји угао већи од 180 степени између две суседне тачке, а у супротном не постоји. Сада можемо да одговарамо на питања да ли се тачка $P$ налази у конвексном омотачу скупа тачака и да подржимо убаивање и избацивање тачака тако што држимо тачке у $\text{std::set}$-у сортиране по углу. Тачке можемо да поредимо по углу ако гледамо у којем квадранту се налазе и ако гледамо знак векторског производа за тачке у истом квадранту. Када убацујемо тачку две тачке престају да буду суседне и добијамо нова два пара суседних тачака па треба да ажурирамо информацију о томе да ли постоји угао већи од 180 степени. Слично тако код избацивања тачке избацујемо два пара из разматрања и убацујемо један. Један изузетак на који треба пазити је случај када се нека тачка поклапа са $P$ и можемо да чувамо информацију о броју таквих тачака и да их не убацујемо у $\text{std::set}$. Када уз помоћ ове структуре урадимо **two pointers** и нађемо границе $G_i$, на упите лако можемо одговорити упоређивањем $G_{L_i}$ и $R_i$. Временска сложеност овог решења је $O(NlogN)$