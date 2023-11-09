## Анализа

Као и већина других _output only_ проблема, овај задатак захтева детаљнију анализу приложених фајлова и тестирање различитих решења на датим тест примерима. Решење не мора бити претерано временски и меморијски ефикасно, једино је важно да се програм изврши у неком догледном времену како би могле да се тестирају и друге стратегије. Основна идеја алгоритма који је користила комисија је максимизовање броја језера фарбањем једног језера (једне повезане компоненте воде) попут шаховске табле. На тај начин од једног језера величине $X$, добићемо отприлике $\frac{X}{2}$ језера, са приближно толико утрошеног материјала. Пошто је очигледно да нећемо моћи да прекријемо сва језера на овај начин, нећемо имати довољно материјала, морамо на неки начин да одредимо која језера су најоптималнија за прекривање. За решавање овог подзадатка можемо користити динамичко програмирање и проблем ранца. Ранац би имао укупну запремину $K$, предмети су у овом случају еквивалентни језерима, тежине предмета би биле једнаке броју поља која морамо трансформисати из воде у земљу да би добили шаховску таблу, док би зарађени новац био еквивалентан броју језера која смо добили преграђивањем велике компоненте. Након бирања неких оптималних компоненти и њиховог фарбања, проћићемо кроз сва офарбана језера још једном и уклонити поља која су вишком промењена. Може се десити да неко поље нема потребе претварати у земљу, зато што је рецимо већ окружено земљом и уништили смо једно језеро, на тај начин мало рушимо изглед шаховске табле али је јасно да број језера не смањујемо и добијамо додатни материјал који можемо искористити.

Поставља се питање шта додатно можемо одрадити са преосталим материјалом, који нисмо искористили у првом бојењу или смо додатно уклонили. Наравно и њега је потребно расподелити на одређена места. Стратегија којом смо се водили у овом случају је, преграђивање неког од тренутних језера на два језера где би величина другог језера била $1 \times 1$. Овде можемо запамтити за свако поље воде колико је потребно додавања земље да би се оно оградило (тај број може ићи од $1$ до $4$). У сваком потезу ћемо бирати језеро коме недостаје најмање поља да буде ограђено(требало би да се може лако показати да ће увек постојати водено поље коме неће недостајати више од $2$ поља земље). 

У приложеним материјалима имате још неколико стратегија решавања овог проблема, треба обратити пажњу на стратегију која користи _BFS_ у одређивању оптималног решења. Она је имала најбоље резултате на неким од примера, али је поприлично спора и на решење се треба чекати и до $10$ минута.

Сложеност описаног алгоритма је $O(k \times BrojJezera)$.

## Смернице за алгоритам

Први део бојења језера попут шаховске табле можемо урадити једноставно коришћењем законитости да сва поља на шаховској табли исте боје дају уједно и исти остатак при дељењу са два њихових координата - $(i+j) mod 2$. Важно је пробати бојење и парних и непарних поља и на неки начин изабрати бољу од опција. Део са динамичким програмирањем и ранцем може бити врло меморијиски захтеван, тако да се мора осмислити пажљиво алгоритам за уклањање једне координате из динамичке матрице. Идеја коју смо користили је рачунање низа парова $DP[i]$, који би давао информацију о максималном резултату који можемо добити ако смо офарбали не више од $i$ поља и из ког стања смо дошли до ове позиције. Друга вредност нам помаже око даље реконструкције језера за бојење. За последњи део и фарбање језера може се користити нека од структура која би памтила поља са тачно $i$ потребних ограђивања, која би могла лако да брише бројеве из скупа и да их поново убацује у други скуп. Детање имплементације можете видети у приложеним кодовима.

Волели бисмо да чујемо и ваше идеје за овај задатак, тако да будите слободни и напишите ако вас је заинтересовао.