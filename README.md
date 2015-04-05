# Runge-Kutta
A method of numerically integrating ordinary differential equations by using a trial step at the midpoint of an interval to cancel out lower-order error terms.

##RK4: classical Runge–Kutta method

Let an initial value problem be specified as follows.

$$
 \dot{y} = f(t, y), \quad y(t_0) = y_0. 
$$

Here, $y$ is an unknown function (scalar or vector) of time $t$ which we would like to approximate; we are told that $\dot{y}$, the rate at which $y$ changes, is a function of $t$ and of $y$ itself. At the initial time $t_0$ the corresponding y-value is $y_0$. The function $f$ and the data $t_0$, $y_0$ are given.

Now pick a step-size $h>0$ and define

$$
\begin{align}
y_{n+1} &= y_n + \tfrac{h}{6}\left(k_1 + 2k_2 + 2k_3 + k_4 \right)\\
t_{n+1} &= t_n + h \\
\end{align}
$$

for $n = 0, 1, 2, 3, . . . $, using

$$
\begin{align}
k_1 &= f(t_n, y_n),
\\
k_2 &= f(t_n + \tfrac{h}{2}, y_n + \tfrac{h}{2} k_1),
\\
k_3 &= f(t_n + \tfrac{h}{2}, y_n + \tfrac{h}{2} k_2),
\\
k_4 &= f(t_n + h, y_n + hk_3).
\end{align}
$$

Here $y_{n+1}$ is the RK4 approximation of $y(t_{n+1})$, and the next value $(y_{n+1})$ is determined by the present value $(y_n)$ plus the weighted average of four increments, where each increment is the product of the size of the interval, $h$, and an estimated slope specified by function $f$ on the right-hand side of the differential equation.

| ---- |:--------------------------------------------------------------------------:| -------------------------|
|$k_1$ |is the increment based on the slope at the beginning of the interval, using | ${y}$ , (Euler's method)
|$k_2$ |is the increment based on the slope at the midpoint of the interval, using  | ${y} + \tfrac{h}{2}k_1$
|$k_3$ |is again the increment based on the slope at the midpoint, but now using    | ${y} + \tfrac{h}{2}k_2$
|$k_4$ |is the increment based on the slope at the end of the interval, using       | ${y} + hk_3$

In averaging the four increments, greater weight is given to the increments at the midpoint. If the weights are chosen such that if $f$ is independent of $y$, so that the differential equation is equivalent to a simple integral, then *RK4* is Simpson's rule.

The *RK4* method is a fourth-order method, meaning that the local truncation error is on the order of $O(h^5)$, while the total accumulated error is order $O(h^4)$.

####Example:
Given the example Differential equation:

$$
y'(t) = t \times \sqrt {y(t)}
$$

With initial condition: $t0 = 0$ and $y0 = y(t0) = y(0) = 1$

This equation has an exact solution:

$$
y(t) = \tfrac{1}{16}(t^2 +4)^2
$$

Demonstrate the commonly used explicit fourth-order Runge–Kutta method to solve the above differential equation.
Solve the given differential equation over the range $t = 0 \ldots 10$ with a step value of $δt = 0.1$ (101 total points, the first being given)

The calculated values of $y$ at whole numbered t's $(0.0, 1.0, \ldots 10.0)$ along with error as compared to the exact solution.

Method summary
Starting with a given $y_n$ and $t_n$ calculate:

$$
\delta y_1 = \delta t\times y'(t_n, y_n)\quad
\delta y_2 = \delta t\times y'(t_n + \tfrac{1}{2}\delta t , y_n + \tfrac{1}{2}\delta y_1)
\delta y_3 = \delta t\times y'(t_n + \tfrac{1}{2}\delta t , y_n + \tfrac{1}{2}\delta y_2)
\delta y_4 = \delta t\times y'(t_n + \delta t , y_n + \delta y_3)\quad
$$

then:

$$
y_{n+1} = y_n + \tfrac{1}{6} (\delta y_1 + 2\delta y_2 + 2\delta y_3 + \delta y_4)
t_{n+1} = t_n + \delta t\quad
$$
