# Задача 2, Вариант 2

Введем события 
$A_i = \\{ X = i \\}, \quad B_i = \\{ Y = i \\},\quad i \ge 0$

Известно, что для любых $i \ge 0$ и $j \ge 0$ события $A_i$ и $B_j$ независимы.  
При этом:

$$
P(X = i) = e^{-\lambda} \frac{\lambda^i}{i!}, \quad \lambda > 0,  i \ge 0,
$$

$$
P(Y = j) = e^{-\mu} \frac{\mu^j}{j!}, \quad \mu > 0, j \ge 0.
$$

Найти:

$$
P(X = i \mid X + Y = j)
$$


---

## Решение

По определению условной вероятности

$$
P(X = i \mid X + Y = j) = \frac{P(X = i, X + Y = j)}{P(X + Y = j)}
$$

Так как $X + Y = j$ и $X = i \Rightarrow Y = j - i$, имеем:

$$
P(X = i \mid X + Y = j) = \frac{P(X = i, Y = j - i)}{P(X + Y = j)}
$$

---

Так как $X$ и $Y$ независимы, их совместная вероятность равна произведению:

$$
P(X = i, Y = j - i)
= P(X = i) \cdot P(Y = j - i)
= e^{-\lambda} \frac{\lambda^i}{i!} \cdot e^{-\mu} \frac{\mu^{j-i}}{(j-i)!}
$$

Получаем 

$$
P(X = i, Y = j - i)
= e^{-(\lambda + \mu)} \frac{\lambda^i \mu^{j-i}}{i! (j - i)!}
$$

---

Найдём знаменатель в формуле условной вероятности:

$$
P(X + Y = j) = \sum_{k=0}^{j} P(X = k) \cdot P(Y = j - k)
$$

Так как $X$ и $Y$ — независимые пуассоновские случайные величины, подставляем их вероятности:

$$
P(X + Y = j)
= \sum_{k=0}^{j} \left( e^{-\lambda} \frac{\lambda^k}{k!} \right)
                 \left( e^{-\mu} \frac{\mu^{j-k}}{(j-k)!} \right)
$$

Вынесем общий множитель $e^{-(\lambda + \mu)}$:

$$
P(X + Y = j)
= e^{-(\lambda + \mu)} \sum_{k=0}^{j} \frac{\lambda^k \mu^{j-k}}{k!(j-k)!}
$$

Заметим, что выражение под знаком суммы связано с биномиальным разложением:

$$
(\lambda + \mu)^j = \sum_{k=0}^{j} \binom{j}{k} \lambda^k \mu^{j-k}
= \sum_{k=0}^{j} \frac{j!}{k!(j-k)!} \lambda^k \mu^{j-k}
$$

Следовательно:

$$
\sum_{k=0}^{j} \frac{\lambda^k \mu^{j-k}}{k!(j-k)!}
= \frac{(\lambda + \mu)^j}{j!}
$$

Подставляем это в формулу:

$$
P(X + Y = j)
= e^{-(\lambda + \mu)} \cdot \frac{(\lambda + \mu)^j}{j!}
$$

Таким образом, сумма независимых пуассоновских случайных величин также распределена по Пуассону:

$$
X + Y \sim \mathrm{Pois}(\lambda + \mu)
$$


---

Подставляем в формулу условной вероятности:

$$
P(X = i \mid X + Y = j) =
\frac{e^{-(\lambda + \mu)} \dfrac{\lambda^i \mu^{j-i}}{i! (j-i)!}}
{e^{-(\lambda + \mu)} \dfrac{(\lambda + \mu)^j}{j!}}
$$

Сокращаем множитель $e^{-(\lambda + \mu)}$:

$$
P(X = i \mid X + Y = j) =
\frac{\lambda^i \mu^{j-i}}{i!(j-i)!}
\cdot
\frac{j!}{(\lambda + \mu)^j}
$$

---

Группируем множители:

$$
P(X = i \mid X + Y = j)
= \frac{j!}{i!(j-i)!}
\left( \frac{\lambda}{\lambda + \mu} \right)^i
\left( \frac{\mu}{\lambda + \mu} \right)^{j-i}
$$

---

## Ответ

Таким образом, условное распределение $X$ при фиксированном $X + Y = j$ имеет биномиальный закон:

$$
X \mid (X + Y = j) \sim \mathrm{Bin}\left(j, \frac{\lambda}{\lambda + \mu}\right)
$$

а вероятность равна:

$$
P(X = i \mid X + Y = j)
= \binom{j}{i}
\left( \frac{\lambda}{\lambda + \mu} \right)^i
\left( \frac{\mu}{\lambda + \mu} \right)^{j-i}
$$
