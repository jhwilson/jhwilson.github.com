---
layout: post
title: Pulsing a two-band model to discover topology
published: true
---

In systems with an anomalous quantum Hall effect, the quantized Hall conductivity comes from the integral of a Chern number over some manifold. Usually, this integral is derived via Kubo formula.
However, there is geometry involved in how the state evolves, and in fact, we can use the dynamics of the current following a weak pulse in order to find the DC conductivity. The route is easy enough: Say we have a conductivity which when written with respect to time is {% m %}\sigma_{xy}(t-t'){% em %}, and without loss of generality we apply a pulse {% m %}E_x(t) = A_x\delta(t){% em %}, then we can find the current response in the perpendicular direction
<!--more-->

{% math %}\begin{align} j_y(t) = \int dt \, \sigma_{yx}(t-t') E_x(t') = \sigma_{yx}(t) A_x. \end{align}{% endmath %}

This allows us to derive an expression for the DC-conductivity

{% math %}\begin{align} \sigma_{yx} = \int dt \, \sigma_{yx}(t) = \frac1{A_x} \int dt \, j_y(t). \end{align}{% endmath %}

Geometrically, there is a lot going on with {% m %}j_y(t){% em %} when we have a system with spin-orbit coupling. In particular, take the two band model

{% math %}\begin{align}
  h(\mathbf p) = \mathbf d(\mathbf p) \cdot \sigma,
\end{align}{% endmath %}

where {% m %}\mathbf d{% em %} is 3D, {% m %}\mathbf p{% em %} is 2D, and {% m %}\sigma = (\sigma_x, \sigma_y, \sigma_z){% em %}, the vector of Pauli matrices. The initial states of the system can be represented by where they are on the Bloch sphere {% m %}-\hat{\mathbf d}(\mathbf p){% em %}. But once a pulse is supplied, this state will begin to rotate about a different vector {% m %}\mathbf d(\mathbf p - e \mathbf A){% em %}. Thus, if we add time dependence to {% m %}\hat{\mathbf d}(\mathbf p, t)\equiv -\langle \sigma(t) \rangle{% em %} to represent the state's location, we can use Heisenberg's equations of motion to obtain

{% math %}\begin{align}
  \hbar \frac{\partial \hat{\mathbf d}(\mathbf p, t)}{\partial t} = 2\mathbf{d}(\mathbf p - e\mathbf A) \times \hat{\mathbf{d}}(p, t).
\end{align}{% endmath %}

We can rewrite this equation as

{% math %}\begin{align}
  \hat{\mathbf d}(\mathbf p,t) = \hat{\mathbf d}(\mathbf p - e \mathbf A) [\hat{\mathbf d}(\mathbf p - e \mathbf A) \cdot \hat{\mathbf d}(\mathbf p)] - \hbar \frac{\hat{\mathbf d}(\mathbf p-e \mathbf A) \times \frac{\partial \hat{\mathbf d}(\mathbf p, t)}{\partial t}}{2d(\mathbf p - e A)}
\end{align}{% endmath %}

However, this state has an associated current with it, and that can be represented by the operator {% m %}j_\mu = -e \partial_\mu \mathbf d(\mathbf p- e \mathbf A) \cdot \sigma{% em %}. And the vector {% m %}\langle\sigma\rangle = -\hat{\mathbf{d}}(p,t){% em %}. Therefore,

{% math %}
\begin{align}
  \langle j_\mu \rangle = e^2 \partial_\mu \mathbf d(\mathbf p - e\mathbf A ) \cdot \hat{\mathbf d}(\mathbf p, t)
\end{align}
{% endmath %}

Combining these expressions, we have
{% math %}
\begin{multline}
\langle j_\mu \rangle = e^2 \partial_\mu \mathbf d(\mathbf p - e\mathbf A ) \cdot \Bigg[ \hat{\mathbf d}(\mathbf p - e \mathbf A) [\hat{\mathbf d}(\mathbf p - e \mathbf A) \cdot \hat{\mathbf d}(\mathbf p)] \\ - \hbar \frac{\hat{\mathbf d}(\mathbf p-e \mathbf A) \times \frac{\partial \hat{\mathbf d}(\mathbf p, t)}{\partial t}}{2d(\mathbf p - e A)}  \Bigg].
\end{multline}
{% endmath %}

Or simplified
{% math %}
\begin{multline}
\langle j_\mu \rangle = e^2 \partial_\mu d(\mathbf p - e\mathbf A )[\hat{\mathbf d}(\mathbf p - e \mathbf A) \cdot \hat{\mathbf d}(\mathbf p)] \\ - \frac{e^2}{2}  \partial_\mu \hat{\mathbf{d}}(\mathbf p - e \mathbf A) \cdot \left[\hat{\mathbf d}(\mathbf p-e \mathbf A) \times \frac{\partial \hat{\mathbf d}(\mathbf p, t)}{\partial t} \right].
\end{multline}
{% endmath %}

This is exact. At this point, we make a couple of approximations. First of all, the first term is independent of {% m %}t{% em %} so it cannot contribute to the total current *if* we have a finite DC conductivity. This leaves the second term. We can do the integral over time --- there is an order of limits problem but we can get around this by noting that we do not expect the infinite time state to contribute to the energy (or: it averages to something proportional to {% m %}\mathbf d(\mathbf p - e \mathbf A){% em %} anway and so the cross product vanishes), so we discard it and therefore, {% m %}\int_0^\infty dt' \, \mathbf d(\mathbf p, t') = - \mathbf d(\mathbf p){% em %}.

Hence, we get the Hall conductivity

{% math %}\begin{align}
  \sigma_{yx} = \frac{e^2\hbar}{2 A_x} \int \frac{d^2 p}{h^2}  \partial_y \hat{\mathbf{d}}(\mathbf p - e \mathbf A) \cdot \left[\hat{\mathbf d}(\mathbf p-e \mathbf A) \times \hat{\mathbf d}(\mathbf p) \right].
\end{align}{% endmath %}

At this point, we actually have not expanded in terms of {% m %}A_x{% em %} yet. The first term will produce a term that is symmetric in {% m %}x{% em %} and {% m %}y{% em %}---however it drops out due to the cross product {% m %}\hat{\mathbf d}(\mathbf p) \times \hat{\mathbf d}(\mathbf p) = 0{% em %} vanishes. Thus, only the second term persists and we see directly that {% m %}x{% em %} and {% m %}y{% em %} must be different and in fact, we get the well-known formula

{% math %}\begin{align}
 \sigma_{yx}^{\mathrm{Hall}} =\frac{e^2}{h} \int \frac{d^2 p}{4\pi}  \hat{\mathbf{d}}(\mathbf p) \cdot \left[\partial_y \hat{\mathbf d}(\mathbf p) \times \partial_x  \hat{\mathbf d}(\mathbf p) \right].
\end{align}{% endmath %}

This describes the Chern number of some manifold parametrized by {% m %}\mathbf p{% em %} (usually the Brillioun zone). It is the number of times the vector {% m %}\mathbf d{% em %} wraps the sphere.

To understand why it's a topological invariant, note that the quantity in the integral looks very much like a Jacobian. In fact, it is; it describes a coordinate transformation from the {% m %}\hat {\mathbf d}{% em %} to {% m %}(p_x,p_y){% em %}.
In this way, the integrand represents an area element on the sphere, and in general {% m %}\mathbf p{% em %} is a closed manifold. So {% m %}\mathbf d(\mathbf p){% em %} maps that closed manifold to the sphere, and without any edges or boundaries the area it maps out must be {% m %}4 \pi{% em %} times an integer.

This formula is well-known, but this dynamical way of obtaining it is slightly less well-known. We have extended this idea in a paper published [last year][1] to handle the out-of-equilibrium case of quenches. In that situation, new phenonmena appear that are quite different from the equilibrium case---terms that we discarded in this calculation become quite relevant.

[1]:http://journals.aps.org/prl/abstract/10.1103/PhysRevLett.117.235302
