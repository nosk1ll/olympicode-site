# Решење задатка Шаховска трка.

Главна идеја је да се направи граф од $5*h*w$  чворова где свака позиција на табли има по 5 чворова (један за сваку фигуру). Гране у овом графу представљају све потезе које можемо да направимо и имају тежину од 1 до 5. Како би избегли $MLE$, ове гране не треба да чувамо у меморији него да прођемо кроз њих итеративно када посматрамо неки чвор.
Једно од решења пушта $Dijkstrin~algoritam$ на овом графу како би се нашла удаљеност свих чворова од чрвора који представља краља на позицији $(1,1)$. 
Како би убрзали алгоритам, током пролажења кроз сва поља на која може краљица/топ/ловац да оде у неком смеру, поред услова да се прекине претрага када се стигне на блокирано поље, треба увести услов да се прекине претрага ако се стигне на поље које има исту или мању удаљеност од удаљености тренутног поља (не рачунајући тренутно поље).
Временска сложеност: $O(n^3 * log n)$, Меморијска сложеност: $O(n^2)$.
Још једна оптимизација програма која није била потребна за $100$ бодова је да се уместо $Dijkstrinog~algoritma$ пусти $Dialov~algoritam$.
Временска сложеност: $O(n^3)$, Меморијска сложеност: $O(n^2)$.