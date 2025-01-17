## Анализа

Кључно је увидети да је најефикаснији начин за решавање овог проблема коришћење листи (или пак двостраних редова) као структуре података за чување слова. Прецизније говорећи, неопходне су две овакве структуре у којима би се у сваком тренутку чувале и одржавале прва, односно друга половина тренутног низа слова.

Свако (непарно) убацивање новог слова заправо представља додавање новог члана на крај једне листе (реда), при чему треба водити рачуна да се приликом сваког другог (тј. парног) додавања, први члан те листе (реда) избаци и дода на крај прве листе (реда). Тиме би обе листе (реда) у сваком тренутку биле или подједнаке дужине или би се разликовале највише за један члан.

Операција замене редоследа прве и друге половине се своди на тривијалну замену два показивача и одвија се само када су листе (редови) једнаких дужина. Како се додавање и пребацивање чланова, као и промена места над овим структурама података могу урадити у константној сложености, $\mathcal{O}(1)$, и како укупно имамо $N$ оваквих операција, тако је, рачунајући ту и крајње исписивање резултата, задатак на овај начин решен у линеарној $\mathcal{O}(N)$ временској сложености.
