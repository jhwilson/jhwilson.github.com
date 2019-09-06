---
layout: post
title: Current in Single Particle Quantum Mechanics
---

For simplicity, I will only use one-dimension in this post, but this can be generalized to higher dimensions rather easily.

Many textbooks on Quantum Mechanics mention current density can be derived from the continuity equation and probability.
The usual method for figuring this out is to assume you have some Hamiltonian {% m %} H = p^2/2m + V(x){% em %} where {% m %}p{% em %} is the momentum and {% m %}x{% em %} is the position.
In this way the current density is written in terms of the wave function {% m %}\psi(x,t){% em %} as
<!--more-->

{% math %}
j(x,t) = \frac1{2m i}\left[ \psi^* \overrightarrow{\partial_x} \psi - \psi^* \overleftarrow{\partial_x} \psi \right].
{% endmath %}

This then satisfies the continuity equation

{% math %}
\partial_t \rho(x,t) + \partial_x j(x,t) = 0,
{% endmath %}

with density {% m %}\rho(x,t)=\psi^*(x,t)\psi(x,t){% em %}. It should be noted that if you write the wave function as {% m %}\psi(x,t) = \sqrt{\rho(x,t)} e^{i \theta(x,t)}{% em %}, then the current is just proportional to the gradient of the phase {% m %}j(x,t)= \rho(x,t) \partial_x \theta(x,t)/m{% em %}, giving the spatial change in phase a physical significance.

However, there are two lingering questions:

1.  Is this current density related to the Heisenberg operator {% m %}\dot x(t){% em %} which tracks the velocity of the system?
2.  If so, does it generalize to more arbitrary Hamiltonians?

To answer these questions, we consider the more arbitrary Hamiltonian

{% math %}
H = T(p) + V(x),
{% endmath %}

where {% m %}V(x){% em %} is some potential and the kinetic energy is some polynomial

{% math %}T(p) = \sum_{n=1} a_n \frac{p^n}{n!}.{% endmath %}

We are unworried about bounding the energy, so odd-order Kinetic energy terms are allowed (in the higher dimensional case, the Dirac-like Hamiltonians have linear terms in {% m %}p{% em %}).
At this point, we can take our Heisenberg operator {% m %}\dot x(t){% em %} and find

{% math %}
\begin{align*}
\dot x(t) & = i [H, x(t)] \\
  & = T'(p(t)).
\end{align*}
{% endmath %}

where {% m %}T'{% em %} is the derivative of {% m %}T{% em %} with respect to its argument.
Now, we would like to obtain a current density from this quantity.
We can certainly define the total current at a specific time as

{% math %}
\begin{align*}
I & = \langle\psi_0\lvert \dot x(t) \rvert \psi_0\rangle = \langle\psi_0\lvert T'(p(t)) \rvert \psi_0\rangle\\
 & = \langle\psi(t)\lvert T'(p) \rvert \psi(t)\rangle,
\end{align*}
{% endmath %}

where in the last line we go from the Heisenberg to Schroedinger picture. Now to get density, we need to use a complete set position states, so that

{% math %}
\begin{align} \label{eq:total-current} \tag{1}
I & = \int dx \, dy \, \langle\psi(t)\lvert x\rangle \langle x \lvert T'(p) \rvert y \rangle \langle y \lvert \psi(t)\rangle.
\end{align}
{% endmath %}

Now, {% m %}p{% em %} acts as a derivative on position kets, so that one can verify that

{% math %}
\langle x \lvert T'(p) \rvert y \rangle = T'(-i \partial_x ) \delta(x-y).
{% endmath %}

However, there is an ambiguity here since we can write

{% math %}
\begin{align}
T'(-i \partial_x)\delta(x-y) & =  \sum_{n=0} a_{n+1} \frac{(-i\partial_x)^n}{n!} \delta(x-y) \nonumber \\ & = \sum_{n=0} a_{n+1} \frac{(-i\partial_x)^{n-m} (i \partial_y)^m}{n!} \delta(x-y). \label{eq:T-delta} \tag{2}
\end{align}
{% endmath %}

This ambiguiuty in how to choose the derivatives leaves us with many way to define the current density.
Fortunately, only one of these combinations satisfies the continuity equation.
To figure out which one that is, let us reverse engineer the continuity equation to obtain a solution.
The density is {% m %}\rho(x,t) = \psi^*(x,t) \psi(x,t){% em %}, and so using the Schroedinger's equation, we have

{% math %}
\begin{align*}
  i \partial_t \rho(x,t) & = i(\psi^*(x,t) \overleftarrow {\partial_t} \psi(x,t) + \psi^*(x,t) \overrightarrow {\partial_t} \psi(x,t) ) \\
   & = - [\psi^*(x,t)( T(i \overleftarrow{\partial_x} ) - T(-i \overrightarrow{\partial_x} ) )\psi(x,t) ].
\end{align*}
{% endmath %}

Thus, the continuity equation must become

{% math %}
\begin{align*}
  \partial_t \rho(x,t) - i [\psi^*(x,t)( T(i \overleftarrow{\partial_x} ) - T(-i \overrightarrow{\partial_x} ) )\psi(x,t) ] = 0.
\end{align*}
{% endmath %}

If we now assume that we have a current density that takes the form

{% math %} j(x,t) = \psi^*(x,t) \vartheta(\overleftarrow{\partial_x},\overrightarrow{\partial_x}) \psi(x,t), {% endmath %}

and satisfies the continuity equation, {% m %}\partial_t \rho + \partial_x j = 0{% em %}, then we can equate operators to obtain

{% math %}
\begin{align} \label{eq:diff-ops-cty} \tag{3}
\overleftarrow{\partial_x} \vartheta + \vartheta \overrightarrow{\partial_x} = -i [T(i \overleftarrow{\partial_x} ) - T(-i \overrightarrow{\partial_x} ) ].  
\end{align}{% endmath %}

Anticipating the answer, we write the general form of {% m %}\vartheta{% em %} as

{% math %}
\vartheta =  \sum_{n=0} \sum_{m=0}^n (-1)^{m} i^n b_{n,m} \overleftarrow{\partial}{}_x^{n-m} \overrightarrow{\partial}{}_x^m.
{% endmath %}

Then we can take the left hand side Eq. \\eqref{eq:diff-ops-cty} and write

{% math %}
\begin{multline*}
\overleftarrow{\partial_x} \vartheta + \vartheta \overrightarrow{\partial_x} = -i \sum_{n=1} i^n b_{n-1,0} \overleftarrow{\partial}{}_x^{n} - \sum_{n=0} \sum_{m=0}^{n-1} (-1)^m i^n \left[  b_{n,m+1} - b_{n,m} \right] \\ \times \overleftarrow{\partial}{}_x^{n-m} \overrightarrow{\partial}{}_x^{m+1}
+ i \sum_{n=1} (-i)^{n} b_{n-1,n-1} \overrightarrow{\partial}{}_x^{n} .
\end{multline*}
{% endmath %}

On the other hand, we can calculate the right hand side of Eq. \\eqref{eq:diff-ops-cty} to be

{% math %}
-i [T(i \overleftarrow{\partial_x} ) - T(-i \overrightarrow{\partial_x} ) ] = -i \sum_{n=1} a_n i^n \frac{\overleftarrow{\partial}{}_x^n}{n!} + i \sum_{n=1} a_n (-i)^n \frac{\overrightarrow{\partial}{}_x^n}{n!}.
{% endmath %}

Equating the left and right sides, we can just read off that {% m %}b_{n-1,0} = a_n/n!{% em %}, {% m %}b_{n-1,n-1}= a_n/n!{% em %} and {% m %}b_{n,m+1} = b_{n,m}{% em %}, so that {% m %}b_{n,m} = a_{n+1}/(n+1)!{% em %}.

Thus, we have

{% math %}
\vartheta = - \sum_{n=0} \sum_{m=0}^n (-1)^{m} i^n \frac{a_{n+1}}{(n+1)!} \overleftarrow{\partial}{}_x^{n-m} \overrightarrow{\partial}{}_x^m.
{% endmath %}

Returning all the way to when we were considering {% m %}\dot x(t){% em %} as an integral over position,
this suggests that in Eq. \\eqref{eq:T-delta}, we want to consider

{% math %}
\begin{equation*}
T'(-i \partial_x)\delta(x-y)  \\ = \sum_{n=0} \frac{a_{n+1}}{n!} \frac1{n+1}\sum_{m=0}^n (-i\partial_x)^{n-m} (i \partial_y)^m \delta(x-y).
\end{equation*}
{% endmath %}

Given the expression for total current Eq. \\eqref{eq:total-current} and integrating the delta function by parts numerous times, we can replace {% m %}\partial_x{% em %} with {% m %}-\overleftarrow \partial_x{% em %} and {% m %}\partial_y{% em %} with {% m %}- \overrightarrow\partial_x{% em %}, and then the total current is just

{% math %}
I = \int dx \, \psi^*(x,t) \sum_{n=0} \frac{a_{n+1}}{(n+1)!} \sum_{m=0}^n (i \overleftarrow \partial_x)^{n-m} (-i \overrightarrow \partial_x)^m \psi(x,t).
{% endmath %}

which actually integrates the current density! Thus, we have shown that

{% math %}
j(x,t) = \psi^*(x,t) \sum_{n=0} \frac{a_{n+1}}{(n+1)!} \sum_{m=0}^n (i \overleftarrow \partial_x)^{n-m} (-i \overrightarrow \partial_x)^m \psi(x,t),
{% endmath %}

and that

{% math %}\langle \dot x(t) \rangle = \int dx \, j(x,t). {% endmath %}

Indeed, {% m %}\dot x(t){% em %} does track the current of the problem and can even be written as the integral of a current density. Even for the more arbitrary Hamiltonian {% m %}H = T(p) + V(x){% em %}.
