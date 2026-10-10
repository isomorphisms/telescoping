# Roadmap: what is the actual project?

The useful way to read Marius Buliga's work is not chronologically. A large fraction of it can be organized around one question:

> If local scale-changing operations are primitive, what geometry, algebra, and computation can be reconstructed from them?

This file separates that line from other work by Buliga (convexity, dissipation, symplectic bipotentials, fracture mechanics), which is mathematically interesting but not the immediate subject of this repository.

## 1. Geometry first: microscopes instead of coordinates

### Dilatation structures I. Fundamentals

Primary source: https://arxiv.org/abs/math/0608536

A dilation based at a point \(x\), with scale \(\varepsilon\), is written

\[
\delta^x_\varepsilon(y).
\]

In Euclidean space,

\[
\delta^x_\varepsilon(y)=x+\varepsilon(y-x).
\]

Instead of assuming a manifold and then deriving local linearization, Buliga axiomatizes the behavior of these zoom maps themselves. Coherent zooming produces a tangent object.

The key conceptual reversal is:

- ordinary differential geometry: smooth manifold first, tangent algebra second;
- dilation-structure viewpoint: coherent local rescaling first, tangent algebra emerges in the limit.

The resulting tangent need not be a vector space. In sub-Riemannian geometry the natural tangent model is typically a Carnot/conical group.

### Introduction to metric spaces with dilations

Primary source: https://arxiv.org/abs/1007.2362

This is probably the best first technical reading. It gives the metric-space formulation and emphasizes metric profiles, tangent spaces, and groups with dilations.

### Maps of metric spaces

Primary source: https://arxiv.org/abs/1107.2817

This is especially useful for intuition. Buliga describes dilation structures in terms of maps, microscopes, resolution, and coherent changes of viewpoint. For this repository that language is more productive than starting from a wall of axioms.

### Sub-Riemannian geometry from intrinsic viewpoint

Primary source: https://arxiv.org/abs/1206.3093

The target example is important: recover the geometry of a regular sub-Riemannian space intrinsically, without smuggling in ordinary smooth coordinates as the basic mechanism.

## 2. Extract the algebra: emergent algebras

### Emergent algebras

Primary source: https://arxiv.org/abs/0907.1520

The metric is not the whole story. The algebraic core can be formulated using scale-indexed idempotent right quasigroups.

For a scale \(\varepsilon\), write

\[
x\circ_\varepsilon y
\]

for dilation of \(y\) toward \(x\). For fixed \(x,\varepsilon\), the second argument is invertible; write the inverse operation as \(x\bullet_\varepsilon y\).

From these primitive operations one constructs scale-dependent approximate difference, sum, and inverse. Under the uniform limiting hypotheses, these converge as \(\varepsilon\to 0\) to group-like operations in the tangent at \(x\).

This is the reason for the word **emergent**: the group law is not a primitive declaration. It appears from repeated scale operations and limits.

### Infinitesimal affine geometry

Primary source: https://arxiv.org/abs/0804.0135

This develops the resulting affine-like geometry. The important warning is that "affine" here does not mean "silently put everything in a vector space." Noncommutative tangent addition is part of the point.

### COLIN implies LIN for emergent algebras

Primary source: https://arxiv.org/abs/2110.08178

This later paper is useful because it clarifies how restrictive distributivity is. Buliga shows that a right-distributivity condition forces the commutative case, while noncommutative conical/Carnot examples naturally satisfy a one-sided version instead.

This is a good antidote to accidentally assuming vector-space behavior.

## 3. The knot/quandle bridge is structural, not decorative

Idempotent right quasigroups are close to racks and quandles.

Buliga explicitly relates their axioms to Reidemeister moves:

- idempotence corresponds to Reidemeister I;
- right-quasigroup invertibility supports Reidemeister II;
- self-distributivity, when imposed, gives the Reidemeister III/quandle behavior.

Primary source: https://arxiv.org/abs/0907.1520

That makes decorated knot/tangle diagrams a natural syntax for the algebra rather than merely an illustration.

### What is a space?

Primary source: https://arxiv.org/abs/1009.5028

Here decorated crossings are used to present computations in emergent algebras. Buliga also proposes a connection with computation in the front-end visual system.

Treat the mathematical diagram calculus as the solid part. Treat the neuroscience interpretation as a hypothesis/program, not as established physiology.

### Braided spaces with dilations

Primary source: https://arxiv.org/abs/1005.5031

This is the direct meeting point of braided sets, dilation structures, emergent algebras, and sub-Riemannian symmetric spaces.

## 4. From geometric operations to computation

### λ-Scale

Primary source: https://arxiv.org/abs/1205.0139

This explicitly enriches lambda calculus with the scale/dilation operations of emergent algebras. It is an important bridge because it shows that the later graph-rewrite work was not an unrelated change of subject.

### Graphic lambda calculus

Primary source: https://arxiv.org/abs/1305.5786

A graph language is built that can represent:

- untyped lambda calculus;
- computations in emergent algebras;
- Reidemeister moves of locally planar tangle diagrams.

This is the conceptual junction of the repository.

### Zipper logic

Primary source: https://arxiv.org/abs/1405.6095

A graph-rewrite system based on local rewrites, with links to chemlambda and knot-diagram computation.

### Chemlambda and directed interaction combinators

History/relation paper: https://arxiv.org/abs/2007.10288

Artificial chemistry experiments: https://arxiv.org/abs/2003.14332

Project page: https://chemlambda.github.io/

The emphasis shifts toward **strictly local graph rewriting**. Computation is performed by local reactions in graph-like "molecules," with asynchronous/random rewrite schedules possible. Quine graphs and replication-like behavior are experimental phenomena of these rewrite systems.

Do not collapse this into "lambda calculus with a funny drawing." One of the interesting questions is exactly which semantics survive when global bookkeeping is replaced by local graph chemistry.

## 5. A reading order that should actually work

1. \`Maps of metric spaces\` — intuition for zooms.
2. \`Introduction to metric spaces with dilations\` — geometric definitions.
3. \`Emergent algebras\` — algebraic core.
4. Work the Euclidean and Heisenberg examples by hand.
5. \`What is a space?\` — diagrammatic syntax.
6. \`λ-Scale\` — bridge to computation.
7. \`Graphic lambda calculus\`.
8. \`Zipper logic\`.
9. \`Graph rewrites ... chemlambda ... directed interaction combinators\`.
10. Return to \`Dilatation structures I\` and the sub-Riemannian papers once the examples make the axioms feel necessary.

## 6. What "telescoping" should mean here

The repository name can be used for a concrete organizing picture:

\[
X
\xrightarrow{\text{zoom at }x,\varepsilon}
X_{\varepsilon,x}
\xrightarrow{\varepsilon\to0}
T_xX.
\]

At finite scale one has approximate sum/difference/inverse. Down the telescope, these stabilize into tangent operations.

A second telescope runs in the other direction:

\[
\text{dilation gates}
\to
\text{decorated crossings}
\to
\text{graph calculus}
\to
\text{local rewrite chemistry}.
\]

Whether those two telescopes can be implemented using one clean graph representation is a worthwhile software question. It should be tested rather than assumed.
