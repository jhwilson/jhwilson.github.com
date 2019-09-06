---
layout: post
title: The delta-function Potential Lattice
---

I was messing around with some simple problems, and found this simple but illustrative problem. It starts you off in basic quantum mechanics and introduces concepts in a very straightforward way to both get to a more condensed matter perspective while even showing some interesting effects that have experimental consequences (energy bands and band gaps opening).
<!--more-->

We look at the relatively simple problem{% sidenote 'sn-id-galitski' 'This is problem 2.53 in [_Exploring Quantum Mechanics_](http://www.amazon.com/Exploring-Quantum-Mechanics-Collection-Researchers/dp/0199232725) by Galitski, Karnakov, Kogan, and Galitski.'%} of finding the energy spectrum for a particle in the lattice potential

{% math %} U(x) = \alpha\sum_{n=-\infty}^\infty \delta(x - n a).{% endmath %}

{% marginfigure 'mf-id-deltafcnlattice' 'assets/img/Delta-fcn-lattice.png' 'A visual representation of _U(x)_.'%}

The time-independent Schr&ouml;dinger equation takes the form

{% math %} \left[ - \frac{\partial_x^2}{ 2 m} + U(x) \right] \psi(x) = E \psi(x), {% endmath %}

where {% m %}E{% em %} is the energy.

Since we can solve the problem between the delta-functions quite simply ({% m %}U(x) =0 {% em %} there), let us restrict our focus to {% m %}na \lt x \lt (n+1)a{% em %}. Here, the wave function takes on the form

{% math %} \psi(x) = A_n e^{ik(x-na)} + B_n e^{-ik(x-na)},{% endmath %}

where we have {% m %}k = \sqrt{2m E}{% em %}. Now, we can find an operator that commutes with the Hamiltonian so that we can diagonlize it to help solve the problem --- this will be the operator that translates us by {% m %}a{% em %}.

To make this clear, let us abstract things to operators so that we have a momentum operator {% m %}   p{% em %} and a position operator {% m %}   x{% em %}, then we have the commutator {% m %} [   x,   p] = i{% em %}. The operator {% m %}  p{% em %} commutes with functions of {% m %}  x{% em %} as though it were a derivative {% m %}[  p, f(  x)] = -i f'(  x){% em %}, so considering the translation operator {% m %} e^{i a   p }{% em %}, we can write

{% math %} e^{i a   p} U(  x) e^{ - i a   p} = \sum_{n=0}^\infty \frac1{n!} U^{(n)}(  x) a^n = U(  x + a),{% endmath %}

and since {% m %}U(x){% em %} is periodic in {% m %}a{% em %}, we have that {% m %}e^{i a   p} U(  x) e^{ - i a   p} = U(  x){% em %}. Thus, the operator {% m %}  T_a = e^{i a   p}{% em %} commutes with the Hamiltonian and we can simulataneously diagonalize both it and the Hamiltonian. We say {% m %}  T_a \lvert \psi\rangle = e^{i a q} \lvert \psi \rangle {% em %} has _quasi-momentum_ {% m %}q{% em %}. It is important to note that this not the same as real momentum which is not a well-defined quantum number in this problem (that needs translation symmetry).

In other words, we can write our eigenfunctions such that {% m %} \psi(x+a) = e^{i q a} \psi(x){% em %}, and this naturally leads us to relate the coefficients for our eigenfunctions above as

{% math %} A_{n-1} = e^{-i q a} A_n, \quad B_{n-1} = e^{-i q a} B_n. {% endmath %}

Now, we can apply matching conditions at {% m %} x = na{% em %} remembering that our wavefunction should be continuous, but that the delta-function will cause the first derivatives to be discontinuous. The equations for the coefficients are

{% math %}
\begin{align*}
  A_n + B_n &  = e^{i k a} A_{n-1} + e^{-i k a} B_{n-1}, \\
  \left( 1 + \frac{2 i m \alpha}{k} \right) A_n - \left( 1 - \frac{2 i m \alpha}k \right) B_n & = e^{i k a} A_{n-1} - e^{-ik a} B_{n-1},
\end{align*}
{% endmath %}

and if we insert the relation between the coefficients at {% m %}n-1{% em %} and {% m %}n{% em %}, we get a matrix equation

{% math %}
\begin{align*}
  \begin{pmatrix}
    e^{i q a} - e^{i k a} & e^{i q a} - e^{- i k a} \\
    e^{i q a} \left(1 + \tfrac{2 i m \alpha}k \right) - e^{i k a} & - e^{i q a } \left( 1 - \tfrac{2 i m \alpha}k \right) + e^{-ik a}
  \end{pmatrix}
  \begin{pmatrix}
  A_n \\ B_n
  \end{pmatrix} = 0
\end{align*}.
{% endmath %}

This equation has a non-zero solution only if the determinant of the matrix is zero which can be written as

{% math %}
  \cos q a - f(E) = 0 , \quad f(E) = \cos ka + \frac{m \alpha}{k} \sin ka.
{% endmath %}

This is an equation which relates the energy to the quasi-momentum. Since {% m %}\cos q a{% em %} can only be between -1 and 1, this equation only has a solution when {% m %}f(E){% em %} is between -1 and 1. The oscillatory nature of {% m %}f(E){% em %} means that it should pass in this range multiple (in fact, a countable infinite) number of times.

Armed with this equation, we can use {% m %} q{% em %} and an integer to label our energies and we obtain the following energy bands by just solving for {% m %}E{% em %} (setting {% m %}m = 10{% em %}, {% m %} a = 1{% em %}, and {% m %} \alpha = 0.3 {% em %})

{% marginfigure 'mf-id-bands' 'assets/img/Bands-delta-fcn-lattice.png' 'Energy bands in the delta-function lattice.' %}

The dotted lines in this plot represent the spectrum if there were no delta-function potentials (displaced in energy by {% m %} \alpha / a {% em %} for clarity). Notice how the introduction of the delta-functions opens up gaps in this energy spectrum, so that there are some energies that are inaccessible. The gaps actually open up when {% m %}\lvert f(E)\rvert \geq 1{% em %} since there is no solution to our equation there. This energy gap for small {% m %}\alpha{% em %} just goes like {% m %}\alpha/a{% em %}, vanishing as we'd expect when {% m %}\alpha = 0{% em %}.

Notice that in this energy spectrum, we see that if {% m %}q \rightarrow -q{% em %} we get the same energy.

Additionally, if the energy ever goes negative the solutions turn from plane waves {% m %}e^{\pm i k (x-na)}{% em %} into functions localized around the delta functions {% m %}e^{\pm\kappa(x-na)}{% em %}. In fact, the wave functions look like this for a {% m %}q=0{% em %} state:

{% marginfigure 'mf-id-wfcn' 'assets/img/Localized-states-delta-fcn-lattice.png' 'Negative energy localized states in delta-function lattice with alpha less than 0.' %}

These only appear when {% m %}\alpha \lt 0{% em %}, and are related to the fact that the delta-function potential has a bound state. Additionally, only one band can ever have this state. This is due to the fact that the oscillatory sine and cosine change to their non-oscillatory hyperbolic counterparts. However, these states in the delta-function lattice are spread out throughout the crystal, and can not be said to be "localized" to a specific site --- they still all have a definite quasi-momentum.

As with other single particle problems, upon considering the many particle picture, these energy bands get filled up to a set energy level (if we are considering fermions).
