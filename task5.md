# Задача 5, Вариант 2

Дано:

$$
F(x) = (1 - e^{-x^2}) \cdot \mathbf{1}(x \ge 0)
$$

$$
Y = |2 - X|
$$

---

## 1. Найти нормирующие константы и плотность

Проверим свойства функции $F(x)$:

- $\lim_{x \to -\infty} F(x) = 0$
- $\lim_{x \to +\infty} F(x) = \lim_{x \to +\infty} (1 - e^{-x^2}) = 1$
- Функция $F(x)$ не убывает, так как её производная 
  $p(x) = 2x e^{-x^2} \ge 0$ при $x \ge 0$

Все свойства выполнены, следовательно, нормирующая константа **не требуется**.

**Плотность распределения:**

$$
p(x) = F'(x) = 2x e^{-x^2}, \quad x \ge 0
$$

---

## 2. Числовые характеристики $X$

**Математическое ожидание $E[X]$:**

$E[X] = \int_{0}^{\infty} x p(x) dx = \int_{0}^{\infty} 2 x^2 e^{-x^2} dx$

$E[X] = \lim_{a \to \infty} \int_0^a 2 x^2 e^{-x^2} dx$

Интегрируем по частям $\int 2x^2 e^{-x^2} dx = -x e^{-x^2} + \int e^{-x^2} dx$

$E[X] = \lim_{a \to \infty} [-x e^{-x^2}]_0^a + \int_0^\infty e^{-x^2} dx = \int_0^\infty e^{-x^2} dx$

Известно из интеграла Гаусса $\int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}$

Получаем $E[X] = \frac{\sqrt{\pi}}{2} \approx 0.886$
---


**Второй начальный момент $E[X^2]$:**

$E[X^2] = \int_0^\infty x^2 p(x) dx = \int_0^\infty 2 x^3 e^{-x^2} dx$

Подстановкой $t = x^2, dt = 2x dx$: $\int_0^\infty 2 x^3 e^{-x^2} dx = \int_0^\infty t e^{-t} dt$

$\int_0^\infty t e^{-t} dt = \lim_{b \to \infty} [-t e^{-t} - e^{-t}]_0^b = 1$

Получаем $E[X^2] = 1$

---

**Дисперсия $Var(X)$:**

$D[X] = E[X^2] - (E[X])^2 = 1 - \frac{\pi}{4} \approx 0.215$

---

**Среднеквадратичное отклонение $X$:**

$\sigma_X = \sqrt{D[X]} = \sqrt{1 - \frac{\pi}{4}} \approx 0.464$
---


**Мода $Mo$:**

$p'(x) = 2 e^{-x^2} (1 - 2x^2) = 0 \Rightarrow x = \frac{1}{\sqrt{2}} \approx 0.707$
  
---

**Медиана $Me$:**

- $1 - e^{-Me^2} = 0.5 \Rightarrow Me = \sqrt{\ln 2} \approx 0.833$

---

## 3. Асимметрия и эксцесс случайной величины $X$

**Коэффициент асимметрии $\gamma_1$:**

$\gamma_1 = \frac{E[(X - E[X])^3]}{(Var(X))^{3/2}}$

Третий центральный момент:  
  $\mu_3 = E[(X - E[X])^3] = \int_0^\infty (x - E[X])^3 p(x) dx$
  
$(x - E[X])^3 = x^3 - 3 x^2 E[X] + 3 x (E[X])^2 - (E[X])^3$

Интеграл:  
  $\mu_3 = 2 \int_0^\infty x^4 e^{-x^2} dx - 6 E[X] \int_0^\infty x^3 e^{-x^2} dx + 6 (E[X])^2 \int_0^\infty x^2 e^{-x^2} dx - 2 (E[X])^3 \int_0^\infty x e^{-x^2} dx$
  
Известные значения интегралов:  
  $\int_0^\infty x e^{-x^2} dx = 1/2$,  
  $\int_0^\infty x^2 e^{-x^2} dx = \sqrt{\pi}/4$,  
  $\int_0^\infty x^3 e^{-x^2} dx = 1/2$,  
  $\int_0^\infty x^4 e^{-x^2} dx = 3 \sqrt{\pi}/8$
  
Получаем $\mu_3 \approx 0.063$

 Следовательно $\gamma_1 \approx 0.632 > 0$ — распределение правосторонне скошенное
 ---


**Коэффициент эксцесса $\gamma_2$:**

$\gamma_2 = \frac{E[(X - E[X])^4]}{(Var(X))^2} - 3$

Четвёртый центральный момент:  

  $(x - E[X])^4 = x^4 - 4x^3 E[X] + 6 x^2 (E[X])^2 - 4 x (E[X])^3 + (E[X])^4$
  
Приблизительно: $\mu_4 \approx 0.161$

Следовательно $\gamma_2 = \frac{\mu_4}{(Var(X))^2} - 3 \approx 0.483 > 0$ — распределение островершинное


---

## Анализ случайной величины $Y$

### Функция распределения $F_Y(y)$

Так как модуль $y \ge 0$

$F_Y(y) = P(Y \le y) = P(|2 - X| \le y) = P(2 - y \le X \le 2 + y)$

**Случай 1: $0 \le y < 2$**

$F_Y(y) = F(2+y) - F(2-y) = e^{-(2-y)^2} - e^{-(2+y)^2}$

**Случай 2: $y \ge 2$**

$F_Y(y) = F(2+y) - F(0) = 1 - e^{-(2+y)^2}$

**Итого**

- $y < 0$: $F_Y(y) = 0$  
- $0 \le y < 2$: $F_Y(y) = e^{-(2-y)^2} - e^{-(2+y)^2}$  
- $y \ge 2$: $F_Y(y) = 1 - e^{-(2+y)^2}$

### Плотность распределения $p_Y(y)$

**Для $0 \le y < 2$:**

$p_Y(y) = \frac{d}{dy} \big( e^{-(2-y)^2} - e^{-(2+y)^2} \big) = 2(2-y) e^{-(2-y)^2} + 2(2+y) e^{-(2+y)^2}$

**Для $y \ge 2$:**

$p_Y(y) = \frac{d}{dy} \big(1 - e^{-(2+y)^2} \big) = 2(2+y) e^{-(2+y)^2}$


**Итого**

- $0 \le y < 2$: $p_Y(y) = 2(2-y)e^{-(2-y)^2} + 2(2+y)e^{-(2+y)^2}$  
- $y \ge 2$: $p_Y(y) = 2(2+y)e^{-(2+y)^2}$  
- иначе: $p_Y(y) = 0$


<img width="694" height="395" alt="image" src="https://github.com/user-attachments/assets/79d6cc7b-f99a-4ffa-877a-b3b591f93f64" />

<img width="691" height="393" alt="image" src="https://github.com/user-attachments/assets/8c8abe5a-8aa0-4213-b1f8-61ac1d6b9437" />

<img width="691" height="393" alt="image" src="https://github.com/user-attachments/assets/33acd068-4823-4b3f-9486-2f2b440e429d" />

