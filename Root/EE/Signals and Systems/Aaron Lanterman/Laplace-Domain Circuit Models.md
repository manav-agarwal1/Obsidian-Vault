# Resistor
$$
\begin{align*}
&v_{R}(t) &&= R \cdot i_R(t), \\
\implies&V_R(s) &&= Z_R \cdot I_R(s), &&...Z_R = R\\
\end{align*}
$$
**Time Domain**
![[Pasted image 20240121075716.png]]
**Laplace Domain**
![[Pasted image 20240121075804.png]]
***
# Capacitor
*Energy stored in Electrical Field*.
$$
\begin{align*}
&i_C(t) &&= C \cdot \frac{d}{dt} v_C(t), \\
\implies&I_C(s) &&= C \cdot [sV_C(s) - v_C(0^-)], \\
\implies&I_C(s) &&= \frac{V_C(s)}{Z_C} - C \cdot v_c(0^-),  &&...Z_C = \frac{1}{Cs}\\
\text{OR, } \,&I_C(s) + C \cdot v_c(0^-)&&= Cs \cdot V_C(s), \\
\implies& V_C(s) &&= \frac{I_C(s)}{Cs} + \frac{v_c(0^-)}{s}, \\
\implies& V_C(s) &&= Z_C \cdot I_C(s) + \frac{v_c(0^-)}{s}, \\
\end{align*}
$$
**Time Domain**
![[Pasted image 20240121075725.png]]
$$
\begin{align*}
&\frac{1}{C} \cdot \int_{0^-}^{t} i_C(\tau) d\tau &&= \int_{0^-}^{t}\frac{d}{d\tau} v_C(\tau) d\tau, \\
\implies&\frac{1}{C} \cdot \int_{0^-}^{t} i_C(\tau) d\tau &&= v_C(t) - v_C(0^-), \\
\implies&v_C(t) &&= \frac{1}{C} \cdot \int_{0^-}^{t} i_C(\tau) d\tau + v_C(0^-)\\
\end{align*}
$$
This expression can take you to $V_C(s)$ by just taking [[Laplace Transforms]].

**Laplace Domain**
![[Pasted image 20240121080050.png]]
- $\mathcal{L}^{-1}\{Cv_C(0^-)\} = Cv_C(0^-) \delta(t)$
OR
![[Pasted image 20240121080914.png]]
- $\mathcal{L}^{-1}\{\frac{v_C(0^-)}{s}\} = v_C(0^-) u(t)$
***
# Inductor
*Energy stored in Magnetic Field*.
$$
\begin{align*}
&v_L(t) &&= L \cdot \frac{d}{dt} i_L(t), \\
\implies&V_L(s) &&= L \cdot [sI_L(s) - i_L(0^-)], \\
\implies&V_L(s) &&= Z_L \cdot I_L(s) - L \cdot i_L(0^-), &&...Z_l = Ls\\
\text{OR, }&V_L(s) + L \cdot i_L(0^-)&&= Ls \cdot I_L(s), \\
\implies&I_L(s) &&= \frac{V_L(s)}{Ls} + \frac{i_L(0^-)}{s}, \\
\implies&I_L(s) &&= \frac{V_L(s)}{Z_L} + \frac{i_L(0^-)}{s}
\end{align*}
$$
**Time Domain**
![[Pasted image 20240121075736.png]]
$$
\begin{align*}
&\frac{1}{L} \cdot \int_{0^-}^{t} v_L(\tau) d\tau&&= \int_{0^-}^{t}\frac{d}{dt} i_L(\tau) d\tau, \\
\implies&\frac{1}{L} \cdot \int_{0^-}^{t} v_L(\tau) d\tau&&= i_L(t) - i_L(0^-), \\
\implies&i_L(t) &&= \frac{1}{L} \cdot \int_{0^-}^{t} v_L(\tau) d\tau + i_L(0^-), \\
\end{align*}
$$
This expression can take you to $I_L(s)$ by just taking [[Laplace Transforms]].

**Laplace Domain**
![[Pasted image 20240121080108.png]]
- $\mathcal{L}^{-1}\{Li_L(0^-)\} = Li_L(0^-) \delta(t)$
OR
![[Pasted image 20240121080935.png]]
- $\mathcal{L}^{-1}\{\frac{i_L(0^-)}{s}\} = i_L(0^-) u(t)$
***
*So, forms with $\delta(t)$ are not practical but both the forms are mathematically equivalent.*
***
*Eg*.
A version from *Circuit Analysis and Design - Ulaby, Maharbiz, and Furse*, as chosen by Prof Lanterman in his video.
![[Pasted image 20240121084335.png]]
When the switch is open for a long time, **Capacitior** acts as a **Open-Circuit**, and **Inductor** acts as a **Short-Circuit**.
$i_L(0^-) = \frac{12}{24} = 0.5 A$
$V_C(0^-) = 12 \cdot 0.5 V = 6 V$
**Laplace Equivalent** for $t \geq 0$., ie; when switch is closed. $8 \ohm$ **resistor** is by passed.
Picking series model for both cases.
![[Pasted image 20240121084942.png]]
*Units are weird in **Laplace Domain**, so generally texts avoid them*.
$$
\begin{align*}
&\frac{12}{s} + 1 &&= 4I_1 + [2s + 12](I_1 - I_2) \\
\end{align*}
$$
And,
$$
\begin{align*}
&0 &&= \frac{5}{s} I_2 + \frac{6}{s} + [12 + 2s](I_2 - I_1) + 1 \\
\end{align*}
$$
Solve, $I_1$ and $I_2$.
$I_L(s) = I_1(s) - I_2(s)$
We can calculate, **Poles**, then use [[Partial Fractions]].
***
*Eg.* Taken from *Circuit Analysis - Mersereau, Jackson*
![[Pasted image 20240121090012.png]]
OR
![[Pasted image 20240121090124.png]]
***
# Transfer Functions

*Eg.*
![[Pasted image 20240122102438.png]]
We take current as our output.

$$
\begin{align*}
&I_o(s) &&= \frac{V_i(s)}{\frac{1}{Cs} + Ls + R}, \\
& &&= V_i(s)\frac{s}{\frac{1}{C} + Ls^2 + Rs},\\
& &&= V_i(s)\frac{\frac{s}{L}}{s^2 + \frac{R}{L}s + \frac{1}{CL}},\\
\implies&\frac{I_o(s)}{V_i(s)} = H_1(s) &&= \frac{\frac{s}{L}}{s^2 + \frac{R}{L}s + \frac{1}{CL}}\\
\end{align*}
$$
We can call $H_1(s)$ as **Transadmittance**, and it is the [[Transfer Functions]] of our circuit.

*Eg.*![[Pasted image 20240122154150.png]]
$$
\begin{align*}
&V_r(s) &&= \frac{V_i(s) \cdot R}{\frac{1}{Cs} + Ls + R}, \\
& &&= V_i(s)\frac{Rs}{\frac{1}{C} + Ls^2 + Rs},\\
& &&= V_i(s)\frac{\frac{Rs}{L}}{s^2 + \frac{R}{L}s + \frac{1}{CL}},\\
\implies&\frac{V_r(s)}{V_i(s)} = H_{2_R}(s) &&= \frac{\frac{Rs}{L}}{s^2 + \frac{R}{L}s + \frac{1}{CL}}\\
\end{align*}
$$
$\omega_n = \frac{1}{\sqrt{LC}}$
We, have a $s$ in numerator so comparing from forms in [[Canonical Second Order Filters]], this is a **Band-Pass Filter**.

*Eg*.
![[Pasted image 20240122154556.png]]
$$
\begin{align*}
&V_C(s) &&= \frac{V_i(s) \cdot \frac{1}{Cs}}{\frac{1}{Cs} + Ls + R}, \\
& &&= V_i(s)\frac{\frac{1}{C}}{\frac{1}{C} + Ls^2 + Rs},\\
& &&= V_i(s)\frac{\frac{1}{LC}}{s^2 + \frac{R}{L}s + \frac{1}{CL}},\\
\implies&\frac{V_C(s)}{V_i(s)} = H_{2_C}(s) &&= \frac{\frac{1}{LC}}{s^2 + \frac{R}{L}s + \frac{1}{CL}}\\
\end{align*}
$$

This is a **Low-Pass Filter**.

*Eg*.
![[Pasted image 20240122154830.png]]
$$
\begin{align*}
&V_L(s) &&= \frac{V_i(s) \cdot Ls}{\frac{1}{Cs} + Ls + R}, \\
& &&= V_i(s)\frac{Ls^2}{\frac{1}{C} + Ls^2 + Rs},\\
& &&= V_i(s)\frac{s^2}{s^2 + \frac{R}{L}s + \frac{1}{CL}},\\
\implies&\frac{V_L(s)}{V_i(s)} = H_{2_L}(s) &&= \frac{s^2}{s^2 + \frac{R}{L}s + \frac{1}{CL}}\\
\end{align*}
$$
This is a **High-Pass Filter**
***
