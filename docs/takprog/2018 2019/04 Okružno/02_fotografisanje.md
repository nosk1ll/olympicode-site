## Анализа

Практично је у задатку дат сортиран низ од $N$ природних бројева и захтева се промена највише једног члана тог низа тако да се минимизује највећа разлика чланова који су суседни не по индексима, већ по вредностима.

Да би се то постигло, потребно у једном проласку кроз низ одредити највећу разлику између два суседна члана. Та највећа разлика може бити јединствена или нејединствена, а може се појављивати на рубовима (почетак и/или крај) низа и/или у средини низа.

Уколико се највећа разлика суседних чланова низа појављује на почетку, односно на крају низа, могуће је простим изједначавањем првог са другим чланом низа, односно последњег са претпоследњим чланом у потпуности елиминисати ту разлику.

Међутим, за разлику од унутрашњих чланова низа, пажљивом променом рубних чланова не може доћи до повећања максималне разлике. Ова чињеница може се искористити за смањење још неке разлике унутар или на другом крају низа. Наиме, уместо изједначавања рубног члана низа са његовим суседом, овај члан се може искористити за потирање друге највеће разлике. На тај начин, практично је у појединим случајевима могуће елиминисати прве две највеће разлике под условом да се једна од њих налази на рубу низа.

Конкретно, није тешко показати да се до оптималног решења увек долази променом најмањег или највећег члана низа. Од ова два члана неопходно је изменити онај чија је разлика с његовим јединим суседом већа. Измењена вредност треба да умањи највећу разлику у остатку низа, а то је исправно учинити променом на вредност аритметичке средине суседних чланова низа међу којима је разлика највећа.

## Смернице за алгоритам

Може се прво испитати гранични случај од два члана који се једноставно решава изједначавањем вредности било првог члана са другим, било другог са првим. Уколико се пак низ састоји од три и више чланова треба одредити да ли је већа разлика између првог и другог или претпоследњег и последњег члана низа. Потом у једном проласку кроз остатак низа (коме не припада руб низа са већом разликом) одредити највећу разлику између суседних чланова. Једноставном променом вредности рубног члана на вредност аритметичке средине два суседна члана с највећом разликом долазимо до решења задатка. Како у задатку имамо један пролазак кроз низ у којој се тражи највећа разлика суседних чланова сложености $\mathcal{O}(N)$, то је укупна временска сложеност алгоритма линеарна.
