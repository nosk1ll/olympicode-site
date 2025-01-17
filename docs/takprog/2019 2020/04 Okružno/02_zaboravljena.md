За почетак, треба одредити да ли је уопште могуће генерисати таблу
каква се тражи у задатку. Уколико $Т < 2K-1$, очигледно није, јер ни
један играч неће стићи да постави $K$ симбола неопходних за победу. У
супротном, решење увек постоји (што ће бити јасно из алгоритма који га
генерише), осим уколико је $K = 2$ и $T > N \cdot \lceil \frac{N}{2}
\rceil + 1$. Да би доказали да у овом случају нема решења, можемо
поделити таблу на $2 \cross 2$ квадрате и приметити да пре последњег
потеза у сваком од њих може бити највише један `X` и један `O`.

Решење за произвољно $T$ можемо направити од решења где $T = N^2$ (`X`
побеђује у последњем потезу), односно T = N \cdot \lceil \frac{N}{2}
\rceil + 1$ ако $K = 2$, на следећи начин:

* уколико је $T$ парно (`O` треба да победи), заменимо све `X` са `O`
  и обрнуто,
* израчунамо колико ће `X` и `O` бити на табли после $T$ потеза, и
* бришемо симболе док не остане очекиван број, водећи рачуна да не
  обришемо ниједан из низа од $K$ узастопних због ког је један од
  играча победио.
  
Остаје само да конструишемо такво решење. Ово ћемо урадити одвојено за
три случаја: $K = 2$, $K = 3$ и $K > 3$

## $K = 2$

Таблу можемо попунити на следећи начин (наизменични `X` и `O`) у
сваком другом реду (пример за $N = 7$):

~~~
XOXOXOX
*......
OXOXOXO
.......
XOXOXOX
.......
OXOXOXO
~~~

Играч који игра последњи потез игра на поље обележено са `*`.

## $K = 3$

Почећемо од табле на којој ни један играч не побеђује:

~~~
xOXOXOX
XoXOXOX
OXOXOXO
OXOXOXO
XOXOXOX
XOXOXOX
OXOXOXO
~~~

Приметимо да, уколико заменимо поља $(1,1)$ и $(2,2)$ (обележена малим
словима), добијамо таблу на којој `X` побеђује у последњем потезу ако
"за крај" остави $(2, 2)$.

## $K > 3$

Слично као за $K = 3$, почећемо од табле у којој нико не побеђује,
коју конструишемо на следећи начин:

* У првом реду имамо $K-1$ симбола `X`, затим један `O`, па опет $K-1$
  `X`, и тако даље.
* Други ред је исти, са замењеним `X` и `O`.
* Даље редове правимо наизменичним понављањем ова два.
* Уколико је $N$ непарно, да би имали очекивани број `X` и `O`,
  последњи ред чине наизменични `X` и `O`.
  
На пример, за $N = 7, K = 4$:

~~~
XXXXoxX
OOOOXOO
XXXXOXX
OOOOXOO
XXXXOXX
OOOOXOO
XOXOXOX
~~~

Слично као у прошлом случају, можемо заменити први `O` са `X` који се
налази после њега и добити позицију у којој `X` "чува" потез $(1, K)$
за крај и побеђује у последњем потезу.

Уколико $N = K$, не можемо заменити ова два симбола (јер нема ничег
десно од тог `O`). У овом случају, није тешко видети да уместо тога
можемо заменити први `O` са пољем $(3, 1)$.
