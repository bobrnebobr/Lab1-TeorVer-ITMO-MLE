# Задача 6

Пусть случайная величина $R$ имеет распределение Рэлея с плотностью:

$$
f_R(r) = \frac{r}{\sigma^2} e^{-r^2 / (2\sigma^2)} \mathbf{1}_{\{r \ge 0\}},
$$

где $ \sigma > 0 $ — масштабирующий параметр. Пусть также  

$$
\Theta \sim U[0, 2\pi],
$$

и $ R $ и $ \Theta $ независимы.  

Рассмотрим переход из полярной системы координат $(R, \Theta)$ в скалярную $(X, Y)$, где:

$$
X= R \cos \Theta,\ Y=R \sin \Theta
$$

Рассмотрим переход $(R, \Theta) \rightarrow (X, Y)$:

$$
g(t, \theta) \rightarrow (x,y) = (r \cos \theta,r \sin \theta), r \ge 0, \theta \in [0; 2\pi)
$$

Обратный переход будет выглядеть следующим образом:

$$
g^{-1}: (x, y) \rightarrow (r=\sqrt{x^2+y^2}, \theta =\mathrm{atan2}(y, x)
$$

Матрица Якоби:

$$
Dg(r, \theta) =\begin{pmatrix}
\frac{\partial x}{\partial r} & \frac{\partial x}{\partial \theta} \\
\frac{\partial y}{\partial r} & \frac{\partial y}{\partial \theta}
\end{pmatrix}=\begin{pmatrix}
\cos \theta & -r \sin \theta \\
\sin \theta & r \cos \theta
\end{pmatrix},
\qquad
|\det Dg(r, \theta)| = r.
$$

Совместная плотность $(R, \Theta)$ (они независимы):

$$
p_{R, \Theta}(r, \theta) = f_R(r) f_\Theta(\theta)
= \frac{r}{\sigma^2} e^{-r^2/(2\sigma^2)} \cdot \frac{1}{2\pi}, \quad r\ge0, \ \theta\in[0,2\pi].
$$

По формуле в условии:

$$
p_{X,Y}(x,y) = p_{R,\Theta}(g^{-1}(x,y)) \cdot \frac{1}{|\det Dg(r,\theta)|}\Big|_{(r,\theta)=g^{-1}(x,y)}.
$$

Подставляем $ |\det Dg| = r $:

$$
p_{X,Y}(x,y) = \frac{r}{\sigma^2} e^{-r^2/(2\sigma^2)} \cdot \frac{1}{2\pi} \cdot \frac{1}{r} = \frac{1}{2\pi\sigma^2} e^{-r^2/(2\sigma^2)}.
$$

Так как $ r^2 = x^2 + y^2 $, получаем:

$$
p_{X,Y}(x,y) = \frac{1}{2\pi\sigma^2} \exp\Big(-\frac{x^2 + y^2}{2\sigma^2}\Big), \quad (x,y) \in \mathbb{R}^2.
$$

Эта плотность раскладывается:

$$
p_{X,Y}(x,y) = \left(\frac{1}{\sqrt{2\pi}\sigma} e^{-x^2/(2\sigma^2)}\right)
\left(\frac{1}{\sqrt{2\pi}\sigma} e^{-y^2/(2\sigma^2)}\right),
$$

Следовательно, $X$ и $Y$ независимы и принадлежат нормальному распределению:

$$
X \sim N(0, \sigma^2), \quad Y \sim N(0, \sigma^2).
$$
