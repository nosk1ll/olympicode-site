## Анализа

Ово је најлакши задатак са Квалификација чије је решење праволинијско и сложености $O(1)$. Потребно и довољно је уочити да постоје само $4$ начина на која се могу поставити операције па је потребно вратити само $\min\{ a + b + c, a + b \cdot c, a \cdot b + c, a \cdot b \cdot c \}$. Ограничења су таква да решење стаје у $32$-битни цео број. Напоменимо да није лако одрадити анализу случаjева на основу броја позитивних/негативних бројева међу $a$, $b$, $c$; између осталог, проблем праве специјални случајеви када су неки од њих $0$ или $\pm 1$ (нпр. није увек оптимално користити само сабирање ако су сви бројеви позитивни).

Додатно, за први подзадатак је решење увек $а + b + c$ jer за све реалне (а самим тим и целе) бројеве $x, y \geq 2$ важи $(x - 1)(y - 1) \geq (2 - 1)(2 - 1) = 1$ што је еквиваленто са $x + y \leq xy$ што значи да се увек исплати да вршимо сабирање уместо множења.
