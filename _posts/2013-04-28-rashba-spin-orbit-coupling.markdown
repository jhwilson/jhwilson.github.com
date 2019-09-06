---
layout: post
title: Spin-orbit coupled Hamiltonian
---

For applications in many parts of condensed matter physics and cold atoms physics, we use what is known as the Rashba spin-orbit coupled Hamiltonian. This Hamiltoninan is so-named because it couples momentum {% m %}\mathbf{p}{% em %}
to the spin {% m %}\mathbf{S}=\frac12\sigma{% em %} where {% m %}\sigma = (\sigma_x,\sigma_y,\sigma_z){% em %} are the Pauli matrices and {% m %}\mathbf{p}=(p_x,p_y,p_z){% em %} is a vector  of momentum operators:
<!--more-->

{% math %} H = \frac{p^2}{2m} + \alpha (\boldsymbol{\sigma} \times \mathbf{p})\cdot \hat{\mathbf{z}} + \Delta \sigma_z. {% endmath %}

{% m %}m{% em %} is the mass, {% m %}\alpha{% em %} is the spin-orbit coupling strength, and {% m %}\Delta{% em %} is some Zeeman field (it acts as magnetic field on the spin).

In this post, we go through the calculation of the energy spectrum and eigenvectors -- a straight forward exercise in undergraduate linear algebra.

First of all, instead of the normal method of finding eigenvectors, we note that we can rewrite this Hamiltonian in the form

{% math %} H = \frac{p^2}{2m} + \mathbf{b}(p) \cdot \boldsymbol{\sigma} {% endmath %}

where {% m %}\mathbf{b}(p) = (\alpha p_y, -\alpha p_x, \Delta){% em %}. Now, {% m %}\mathbf{b}(p){% em %} represents a point on the Bloch sphere, and so we expect the eigenvectors to be parallel and anti-parallel to this vector. The energies in this case are very straight forward and amount to the positive and negative of {% m %}\lvert\mathbf{b}(p)\rvert{% em %}:

{% math %} \epsilon_\pm(p) = \frac{p^2}{2m} \pm \sqrt{ \alpha^2 p^2 + \Delta^2}. {% endmath %}

With these eigenvalues, it is a straight forward exercise in linear algebra to find the eigenvectors. After a bit of algebra, the eigenvectors of {% m %}H{% em %} in terms of the eigenvectors of {% m %}\sigma_z{% em %} ( {% m %}\sigma_z\left\lvert\uparrow\right\rangle = \left\lvert\uparrow\right\rangle{% em %} and {% m %}\sigma_z\left\lvert\uparrow\right\rangle = -\left\lvert\uparrow\right\rangle{% em %} ) are

{% math %}\left\lvert\pm\right\rangle = \frac1{\sqrt2}\left[\sqrt{1 \pm \frac{\Delta}{\sqrt{\Delta^2+\alpha^2 p^2}}}\left\lvert\uparrow\right\rangle + e^{-i\phi} \sqrt{1 \mp \frac{\Delta}{\sqrt{\Delta^2+\alpha^2 p^2}}}\left\lvert\downarrow\right\rangle \right]{% endmath %}

where we have defined {% m %}\phi{% em %} by {% m %}p_y+ip_x = p e^{i\phi}{% em %}. Note that when {% m %}p_{x,y} \rightarrow -p_{x,y}{% em %}, the occupations stay the same. However, if we just look at one energy, {% m %}\epsilon_-(p){% em %} the ground state energy, we see that the state we get when {% m %}p_{x,y} \rightarrow -p_{x,y}{% em %} is almost orthogonal to the original state.

{% marginfigure 'mf-rashba' 'assets/img/Energy-splitting-rashba-so.png' '' %}
The energy bands themselves look like the figure on the right where the vertical axis is energy (and for this particular example, {% m %}m=1{% em %}, {% m %}\alpha = 3{% em %}, and {% m %}\Delta=2{% em %}). Interestingly, the introduction of {% m %}\Delta{% em %} actually causes the gap to open up -- the dotted lines are for when {% m %}\Delta=0{% em %}.

Now, if we have a bunch of fermions filling up these energies, if we set the chemical potential to be in the gap, we would find that the only excitations would states that are spin-locked to the momentum.

Many things can be done with this Hamiltonian to interesting effect. It finds its way into [cold atom physics](http://arxiv.org/abs/1102.3945) as well as [condensed matter](http://books.google.com/books?hl=en&lr=&id=LQhcSCuzC3IC).
