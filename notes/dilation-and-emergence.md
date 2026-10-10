# Dilation structures and emergent operations

## 1. Primitive operation

Take a point type \(X\), a scale parameter \(\varepsilon\), and a family of maps

\[
\delta^x_\varepsilon : X \to X.
\]

Interpret \(\delta^x_\varepsilon(y)\) as "look at \(y\) from \(x\) at scale \(\varepsilon\)."

Euclidean model:

\[
\delta^x_\varepsilon(y)=x+\varepsilon(y-x).
\]

A useful abstraction is

\[
x\circ_\varepsilon y := \delta^x_\varepsilon(y).
\]

For a fixed base point and scale, the map in \(y\) is invertible. Write

\[
x\bullet_\varepsilon y
\]

for its inverse in the second argument.

The scale law is the obvious one for repeated zoom:

\[
x\circ_\varepsilon(x\circ_\mu y)
=
x\circ_{\varepsilon\mu}y.
\]

The base point is fixed:

\[
x\circ_\varepsilon x=x.
\]

These are the algebraic bones behind the geometric axioms.

## 2. Approximate arithmetic from dilation

For a fixed scale, the idempotent-right-quasigroup formulas give three derived operations.

### Approximate difference

\[
\Delta^x_\varepsilon(u,v)
=
(x\circ_\varepsilon u)
\bullet_\varepsilon
(x\circ_\varepsilon v).
\]

### Approximate sum

\[
\Sigma^x_\varepsilon(u,v)
=
x\bullet_\varepsilon
\big((x\circ_\varepsilon u)\circ_\varepsilon v\big).
\]

### Approximate inverse

\[
\operatorname{inv}^x_\varepsilon(u)
=
(x\circ_\varepsilon u)\bullet_\varepsilon x.
\]

The striking point is that none of \(+\), \(-\), a zero vector, or scalar multiplication had to be assumed as primitive data.

Under the uniformity/limit hypotheses of an emergent algebra or dilation structure,

\[
\Delta^x_\varepsilon \to \Delta^x,\qquad
\Sigma^x_\varepsilon \to \Sigma^x,\qquad
\operatorname{inv}^x_\varepsilon \to \operatorname{inv}^x
\]

as the scale tends to zero. The limiting operations form the local tangent-group structure.

Primary sources:

- https://arxiv.org/abs/0907.1520
- https://arxiv.org/abs/math/0608536

## 3. Euclidean sanity check

Let

\[
x\circ_\varepsilon y=x+\varepsilon(y-x),
\qquad
x\bullet_\varepsilon y=x+\varepsilon^{-1}(y-x).
\]

Then direct calculation gives

\[
\Delta^x_\varepsilon(u,v)
=
x+v-u+\varepsilon(u-x),
\]

so

\[
\Delta^x(u,v)=x+v-u.
\]

Similarly,

\[
\Sigma^x_\varepsilon(u,v)
=
u+v-x-\varepsilon(u-x),
\]

hence

\[
\Sigma^x(u,v)=u+v-x.
\]

And

\[
\operatorname{inv}^x_\varepsilon(u)
=
2x-u+\varepsilon(u-x),
\]

hence

\[
\operatorname{inv}^x(u)=2x-u.
\]

At base point \(x=0\), ordinary vector addition, subtraction, and negation reappear.

This is the simplest possible demonstration of "emergence": ordinary affine arithmetic is recovered from a one-parameter family of contractions.

## 4. Heisenberg group: the first example that matters

Use coordinates \((a,b,c)\) with group law

\[
(a,b,c)(a',b',c')
=
\left(
a+a',
b+b',
c+c'+\frac12(ab'-ba')
\right).
\]

The anisotropic dilations are

\[
\delta_\varepsilon(a,b,c)
=
(\varepsilon a,\varepsilon b,\varepsilon^2 c).
\]

A dilation based at \(p\) is

\[
\delta^p_\varepsilon(q)
=
p\,
\delta_\varepsilon(p^{-1}q).
\]

This is the example to keep beside every abstract definition because it blocks several bad intuitions:

- the tangent "sum" need not commute;
- coordinates need not scale equally;
- the vertical coordinate has weight \(2\);
- commutators of horizontal motions create vertical motion;
- the tangent object is group-like but not a vector space.

For a visualization, draw a small horizontal commutator loop. In Euclidean geometry it closes trivially. In the Heisenberg group the commutator produces displacement in the \(c\)-direction. Under Carnot scaling this is exactly the behavior one wants to preserve.

## 5. Why sub-Riemannian geometry is the motivating case

A regular sub-Riemannian manifold has metric tangents modeled by Carnot groups. Buliga's program is to recover this intrinsically from the metric plus coherent dilations rather than using ordinary smooth coordinates as hidden scaffolding.

Relevant papers:

- Dilatation structures in sub-Riemannian geometry:
  https://arxiv.org/abs/0708.4298
- Characterization via length dilation structures:
  https://arxiv.org/abs/0810.5042
- Sub-Riemannian geometry from intrinsic viewpoint:
  https://arxiv.org/abs/1206.3093

## 6. Idempotent right quasigroups, racks, and quandles

An idempotent right quasigroup has a binary operation \(\circ\) satisfying

\[
x\circ x=x
\]

and, for fixed \(x\), the map \(y\mapsto x\circ y\) is bijective.

This sits close to knot-theoretic algebra:

- right-quasigroup invertibility is tied to undoing a crossing;
- idempotence supplies the Reidemeister-I behavior;
- adding self-distributivity gives the quandle-style Reidemeister-III behavior.

Buliga uses this to move between algebraic formulas and decorated link diagrams.

Primary sources:

- https://arxiv.org/abs/0907.1520
- https://arxiv.org/abs/1009.5028
- https://arxiv.org/abs/1005.5031

## 7. Type-design consequence

The software representation should not begin with vectors.

A minimal abstract interface is closer to:

\`\`\`
Point
Scale

dilate : Point -> Scale -> Point -> Point
\`\`\`

with laws for scale composition, fixed centers, invertibility in the final argument, and convergence.

Only after choosing a base point \(x\) and taking the tangent limit should one expose something like:

\`\`\`
TangentAt x
tangentSum
tangentInverse
tangentDilate
\`\`\`

That separation matches the mathematics and avoids accidentally assuming that every point of the original space lives in a linear space.

## 8. Things to prove/test in code

1. Euclidean derived-operation formulas above.
2. Same formulas over any normed vector space.
3. Heisenberg group dilation composition.
4. Convergence of finite-scale approximate sum/difference/inverse.
5. Noncommutativity of the Heisenberg tangent sum.
6. Reidemeister-I/II identities at the irq level.
7. Reidemeister-III only when the additional distributive law is supplied.
8. A failure test showing that coordinate-wise Euclidean interpolation is the wrong dilation for the Heisenberg geometry.
