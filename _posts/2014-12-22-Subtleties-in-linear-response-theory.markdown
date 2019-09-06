---
layout: post
title: Subtleties in linear response theory
published: true
---

In linear response theory, we consider some small perturbation to a Hamiltonian and look at the response of some observable to that perturbation. In the case considered here, the perturbation is an electric field, and the response is current. The linear response that characterizes these quantities is called the conductance.
<!--more-->

There's a problem though, an electric field _accelerates_ a charge. Consider a classical electron for the time being, then

{% math %}
\begin{align}
m \ddot x(t) = - e \mathbf{E}. \label{eq:Newton} \tag{1}
\end{align}
{% endmath %}

Or in terms of current {% m %}j(t) = -e \dot x(t){% em %}, {% m %} \frac{d j}{dt} = \frac{e^2}{m} \mathbf{E} {% em %}. From here we can quickly and naively go to frequency space to find {% m %} j(\omega) = i \frac{e^2/m}{\omega} \mathbf{E}(\omega) {% em %}. Then one might remember that another way to define {% m %}\mathbf{E}{% em %} is in terms of a vector potential that is purely time-dependent, so {% m %}\mathbf{E}(\omega) = i \omega \mathbf A(\omega){% em %}. Now, if we just plug this into our linear response for the current, we get

{% math %} j(\omega) = - \frac{ e^2}{m} \mathbf A(\omega). \label{eq:jA} {% endmath %}

All is well and good, right? Well, not quite. In electromagnetism, the constant part of {% m %}\mathbf A(t){% em %} corresponds to the {% m %}\omega = 0{% em %} term of {% m %}A(\omega){% em %}. This represents what is known as a "pure gauge". These gauges are _physically equivalent_ to the null field {% m %}\mathbf A(\omega=0) = 0{% em %}. Thus, whatever linear response is represented above at {% m %}\omega = 0{% em %} must be unphysical, right?

Wrong.

Before explainging why this is wrong, let's give some further context to this linear response theory. The term {% m %}- e^2/m{% em %} is actually the single particle term of what is known as the "diamagnetic" response to the conductivity when you add in more electrons (usually distributed in a Fermi distribution). This term persists in quantum mechanics, and no other terms appear to cancel it in the simplest case of {% m %} H = \frac{p^2}{2m} {% em %}. In fact, while the math becomes more cumbersome, the solution we shall illustate below holds perfectly well for even the non-interacting multi-electron system.

Now, at this point you may have guessed that there's something strange going on at {% m %}\omega = 0{% em %} due to the fact that the electric field _accelerates_ the particle and doesn't just have a velocity response. At the {% m %}\omega = 0{% em %} point, the _physical_ field {% m %}E(\omega){% em %} seems to necessarily be equal to zero in the gauge we have prescribed unless {% m %}A(\omega) \sim 1/\omega {% em %} for small {% m %}\omega{% em %}. This would lead to a divergent {% m %}j(\omega){% em %}, restoring our faith that the system is accelerating out of control.

But what about when {% m %}\mathbf{A}(\omega=0) = \mathbf{A}_0{% em %}? It seems like then we have a true velocity response to an unphysical object. The solution is subtle: At some point in the quick derivation we made an assumption that implied {% m %}\mathbf A(t) \rightarrow 0 {% em %} at {% m %} t \rightarrow -\infty{% em %}. This implies that if {% m %}\mathbf A(t) = \mathbf A_0{% em %} at any finite time, there had to be some time in between where {% m %}d\mathbf A/ dt \neq 0{% em %}. Thus, during that "ramp up" time, an electric field was on and it accelerated the charge to a specific velocity resulting in the current {% m %}j(\omega) = - \frac{ e^2}{m} \mathbf A(\omega){% em %}.

The assumption is subtle, but the result is rather simple. For now, just assume that {% m %}\mathbf A(-\infty) = 0 {% em %} and at some {% m %}t_0{% em %}, {% m %}\mathbf A(t_0) = \mathbf A_0{% em %}, then we can integrate Eq. \eqref{eq:Newton} to obtain the velocity:

{% math %} m \dot x (t_0) =  e \int_{-\infty}^{t_0} \frac{d \mathbf A}{d t} d t = e \mathbf A_0. {% endmath %}

Or, in other words, {% m %}\mathbf j(t_0) = -\frac{e^2}{m} \mathbf A_0{% em %}, the same as before! This is how a constant {% m %}\mathbf A_0{% em %} can be physical: When it represents the change from a different constant vector potential.

Now, to isolate the assumption, let us run through what they were

1. {% m %}\frac{d j}{d t} = \frac{e^2}{m} E(t){% em %}.
2. Take the Fourier transform: {% m %} j(\omega) = i \frac{e^2/m}{\omega} E(\omega){% em %}.
3. Insert vector potential with {% m %}E = -\frac{d}{dt} A{% em %} and _assume the Fourier transform exists_ for {% m %}A{% em %}: {% m %}j(\omega) = - \frac{e^2}m A(\omega){% em %}.
4. Undo the Fourier transform: {% m %}j(t) = - \frac{e^2}{m} A(t){% em %}.

Now, let us get the last equation (in #4 above) by a simpler route.

1. {% m %}\frac{d j}{dt} = \frac{e^2}{m} E(t){% em %}.
2. Use {% m %}E = - \frac{d}{dt} A{% em %} and integrate the above expression from {% m %}-\infty{% em %} to {% m %}t{% em %}: {% m %}j(t) - j(-\infty) = -\frac{e^2}{m} ( A(t) - A(-\infty)){% em %}.

Two perfectly legitimate calculations resulting in different results. Firstly, this highlights that the first procedure does actually assume {% m %}A(-\infty) = 0{% em %}. Secondly, the only assumptions that could have given {% m %}j(-\infty) = 0{% em %} (an assumption we probably wanted anyway) and {% m %}A(-\infty) = 0{% em %} are that they could be given in terms of Fourier transforms. In order for a function to have a Fourier transform it needs to be _absolutely integrable_---i.e. {% m %} \int_{-\infty}^\infty \lvert A(t) \rvert dt \lt \infty{% em %}. Given {% m %}A(t){% em %} as a continuous, piece-wise differentiable function, we need {% m %}A(t) \rightarrow 0 {% em %} for {% m %}t \rightarrow \pm \infty{% em %}. This imposes our gauge, and since we are not interested in future times let alone {% m %} t \rightarrow +\infty{% em %}, we can artificially modify the function as we see fit to accomodate that. But how the function began at {% m %}-\infty{% em %} is important, and we must impose that. Hence, we have chosen, at least partially, a gauge.

We are left with a dilemma then about pure plain waves {% m %} A(t) = A(\omega) e^{-i \omega t}{% em %}. How do those function?

Technically, they are outside of the bounds of the Fourier analysis and we can see that simply by the fact that if we tried to do the above procedure, we couldn't have a well defined answer as {% m %}t \rightarrow -\infty{% em %} (too oscillatory). However, we can approximate the plain wave in terms of an absolutely integrable function {% m %} A_\delta(t) = A(\omega) e^{-i (\omega + i \delta) t}{% em %} for any {% m %}\delta \gt 0{% em %}, and everything works. This shows us explicitly that {% m %}t = - \infty{% em %} does have {% m %} A_\delta \rightarrow 0{% em %} for all {% m %}\delta \gt 0{% em %}. And this is the origin of the well known substitution {% m %}\omega \rightarrow \omega + i\delta{% em %}.

The natural question to ask now is how this works for a real system (with dissipation). Why does such a term not exist at zero frequency?

Unless your system is a superconductor, there is some dissipation in the system.
The simplest way to include this is classically: When an electron is going at velocity {% m %}\dot x(t){% em %} it experiences a "drag" that tends to slow it down.
Thus, our Newton's equations become

{% math %} m \ddot x(t) = - m \gamma \dot x(t) - e \mathbf E{% endmath %}

where {% m %}\gamma{% em %} describes how much drag the electron experiences.
For more disorder, this would be a larger number.
Playing the same Fourier transform game, we can obtain rather quickly that

{% math %} j(\omega) = - \frac{e^2}{m} \frac{\omega}{\omega  +i  \gamma}  A(\omega). {% endmath %}

This is just one step away from the well-known [Drude model](http://en.wikipedia.org/wiki/Drude_model).
We see that if {% m %}A(t) = A_0{% em %}, then {% m %}j(\omega) = 0{% em %}.
But our gauge choice that we described before is still in place, the only difference is that our "kick" at {% m %}t=-\infty{% em %} has an infinite time to dissipate back to rest (the inclusion of {% m %}\gamma{% em %} above is critical for {% m %}j(\omega=0) =0{% em %}).
This also suggests a steady state current when {% m %}\mathbf E{% em %} is constant: {% m %}m\ddot x=0{% em %} implies {% m %}j = \frac{e^2}{m \gamma} \mathbf E{% em %}.
Our current relaxes to zero when there's nothing around ({% m %}\mathbf E = 0{% em %}), as we would expect.

When a quantum mechanical description is done---by taking a random disorder potential and averaging over disorder configurations---one obtains similar results.
The diamagnetic term for a _clean system_ is real and has a physically well defined explanation.

One may not be surprised that this curious "diamagnetic term" occurs for superconductors, however it is sometimes explained that "gauge symmetry is broken" and that is why such a term exists.
This is a misleading statement, but one I will explore in a future post.
