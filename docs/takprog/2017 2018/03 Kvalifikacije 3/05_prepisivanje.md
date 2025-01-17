Преписивање

Подзадатак 1

Сложеност 
O
(
K
∑
N
i
=
1
S
i
)
 .
За сваку рунду треба имати листу такмичара који су на њој преписивали. Сваки упит решавамо тако што кренемо од почетне рунде и бројимо оне такмичаре које смо први пут ухватили.

Offline решење

Потребно нам је сегментно стабло. Да би решили све упите којима је почетна рунда S за сваког такмичара који је преписивао на некој од рунди иѕ сегмента [S,R] треба да на вредност прве рунде на којој ће бити ухваћен додамо 1. Да би ефикасно изградили структуру треба да решавамо прво све упите са S=R па S=R-1 итд. Када је S=R вредност R у стаблу биће једнака броју људи који су преписивали на тој рунди. За остале S није довољно само поставити вредност на број људи који су преписивали на тој рунди већ морамо и да смањимо вредност неких од следећих рунди. Ако је такмичар X преписивао на тренутној рунди и на некој од следећих треба да смањимо вредност следеће рунде на којој је преписивао. Овако у сваком кораку имамо описано сегментно стабло. Упите решавамо бинарном претрагом по решењу уз помоћ сегментног стабла. Сложеност овог алгоритма је 
O
(
K
l
o
g
2
R
)
 .

Подзадатак 2

Овај подзадатак се решава тако што уместо обичног сегментног стабла користимо persistent segment tree. Тако можемо приступити претходним верзијама сегментног стабла и после целе изградње. Временска сложеност остаје 
O
(
K
l
o
g
2
R
)
 а меморијска се повећава на 
O
(
(
∑
N
i
=
1
S
i
)
l
o
g
R
)
 .

Подзадатак 3

Овај подзадатак захтева више размишљања. Потребно је смањити сложеност Offline решења са 
O
(
K
l
o
g
2
R
)
 на 
O
(
K
l
o
g
R
)
 . Приметимо да сегментно стабло већ има израчунате вредности за неке сегменте. То можемо користити уместо бинарне претраге. Започнимо рекурзивну алгоритам у корену стабла. Ако је вредност левог сегмента већа или једнака броју такмичара које члан комисије треба да ухвати померамо се на лево подстабло, ако не померамо се на десно подстабло и памтимо да смо ухватили онолико такмичара колика је била вредност левог сегмента. На крају овог алгоритма налазимо се у листу који представља решење упита.

Подзадатак 4

Овај подзадатак се решава применом подзадатака 2 и 3, односно користимо persistent segment tree и описани алгоритам на њему да би смањили временску сложеност на 
O
(
K
l
o
g
R
)
 док меморијска сложеност остаје 
O
(
(
∑
N
i
=
1
S
i
)
l
o
g
R
)
 .

На линку испод је детаљно објашњена persistent segment tree структура података.

GeeksforGeeks – 10 Feb 17 20

Persistent Segment Tree | Set 1 (Introduction) - GeeksforGeeks 20
A Computer Science portal for geeks. It contains well written, well thought and well explained computer science and programming articles, quizzes and practice/competitive programming/company interview Questions.

Задаци за вежбу

Овај трик није ништа ново у такмичарском програмирању. Постоји доста задатака који се решавају на сличан начин.

http://codeforces.com/contest/899/problem/F 46
Овај задатак може да се решава и као подзадатак 2.

http://codeforces.com/problemset/problem/786/C 32
Овај задатак захтева persistent segment tree и трик за смањење сложености.