## 10 Efficient Frontier

Right before transaction on day 𝑡, the portfolio’s return amounts to $u = A u_1 + (1 − A)u_2$, where $A = M(t)/V(t)$ is the proportion of money. If the signal of buying is observed, an investor spends $\tilde{m}=\gamma_U M(t)$ buying $(1 − \xi)\tilde{m}/S(t)$ shares and changes $u$ to $u_U=A_U u_1+(1-A_U)u_2$.

### (1) Express $A_U$ in terms of $V(t)$, $\gamma_U$, $\xi$ and $M(t)$.

$$
\begin{aligned}
A_U &= \frac{M_U}{M_U+N_US}\\
&= \frac{(1-\gamma_U) M}{(1-\gamma_U)M+(N+(1-\xi)\gamma_U M/S)S}\\
&= \frac{(1-\gamma_U) M}{(1-\gamma_U)M+NS+(1-\xi)\gamma_U M}\\
&= \frac{(1-\gamma_U) M}{(1-\gamma_U)M+V-M+(1-\xi)\gamma_U M}\\
&= \frac{(1-\gamma_U) M}{V-\xi\gamma_U M}
\end{aligned}
$$

In contrast, if the signal of selling is observed, an investor sells $\tilde{n} = \gamma_D N(t)$ shares to earn $(1 − \xi)\tilde{n}S(t)$ and changes $u$ to $u_D=A_Du_1+(1-A_D)u_2$.

And then express $1-A_D$ in terms of $V(t)$,$S(t)$,$\gamma_D$, $\xi$ and $N(t)$.

$$
\begin{aligned}
1-A_D &= \frac{N_DS}{N_DS+M_D}\\
&= \frac{(1-\gamma_D)NS}{(1-\gamma_D)NS+(1-\xi)\gamma_D NS+M}\\
&= \frac{(1-\gamma_D)NS}{(1-\gamma_D)NS+(1-\xi)\gamma_D NS+V-NS}\\
&= \frac{(1-\gamma_D)NS}{V-\xi\gamma_D NS}
\end{aligned}
$$

### (2) Express $A_U/A$ and $(1-A_D)/(1-A)$ in term of $\gamma$.

$$
\begin{aligned}
u_U&=\gamma(u_2-u)+u\\
A_U u_1+(1-A_U)u_2&=\gamma(u_2-A u_1 - (1 − A)u_2)+A u_1 + (1 − A)u_2\\
A_U u_1+(1-A_U)u_2&=- \gamma A u_1 + \gamma A u_2 + A u_1 +(1-A) u_2\\
A_U u_1+(1-A_U)u_2&=(1-\gamma)A u_1 + \gamma A u_2 +(1-A) u_2\\
A_U u_1-A_Uu_2&=(1-\gamma)A u_1 + \gamma A u_2 -Au_2\\
A_U (u_1-u_2)&=(1-\gamma)A (u_1 -u_2)\\
A_U/A&=(1-\gamma)\\
\end{aligned}
$$

### (3) Express $\gamma_U$ in terms of {𝛾, 𝑉 (𝑡), 𝑀 (𝑡), 𝜉}

$$
\begin{aligned}
1-\gamma &= \frac{A_U}{A}\\
1-\gamma &= \frac{(1-\gamma_U) V}{V-\xi\gamma_U M}\\
\gamma_U&=\frac{\gamma V}{V-(1-\gamma) \xi M}
\end{aligned}
$$

And express $\gamma_D$ in terms of {𝛾, V(t) ,S(𝑡), 𝑁 (𝑡), 𝜉}

$$
\begin{aligned}
\gamma_D &= \frac{\gamma V}{V-(1-\gamma) \xi NS}
\end{aligned}
$$