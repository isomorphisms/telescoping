# Visual and computational experiments

The first goal should be to make the scale dependence visible. These experiments are ordered by mathematical payoff, not by implementation difficulty.

## Experiment 1: Euclidean telescope

Display four movable points \(x,u,v\) and a logarithmic scale control \(\varepsilon\in(0,1]\).

Render:

\[
\delta^x_\varepsilon(u),\quad
\delta^x_\varepsilon(v),\quad
\Sigma^x_\varepsilon(u,v),\quad
\Delta^x_\varepsilon(u,v),\quad
\mathrm{inv}^x_\varepsilon(u).
\]

Overlay their limiting values:

\[
u+v-x,\qquad x+v-u,\qquad 2x-u.
\]

Show the numerical error versus \(\varepsilon\). In the Euclidean formulas the leading error is linear in \(\varepsilon\), so this gives a trivial but exact acceptance fixture for the renderer and algebra.

## Experiment 2: Heisenberg telescope

Use the Heisenberg group

\[
(a,b,c)(a',b',c')
=
(a+a',b+b',c+c'+\tfrac12(ab'-ba'))
\]

with anisotropic dilation

\[
\delta_\varepsilon(a,b,c)
=
(\varepsilon a,\varepsilon b,\varepsilon^2 c).
\]

Render the same finite-scale operations as in the Euclidean case.

The important visible facts are:

- horizontal directions scale as \(\varepsilon\);
- the central direction scales as \(\varepsilon^2\);
- tangent addition is noncommutative;
- a horizontal commutator produces central displacement.

A camera can exaggerate the \(c\)-coordinate for display while retaining the true coordinates numerically.

This should be the first demonstration that the framework is doing more than affine interpolation.

## Experiment 3: metric-profile zoom

For a pointed metric space \((X,x,d)\), visualize successively rescaled balls

\[
\left(\overline B(x,\varepsilon),\frac{1}{\varepsilon}d\right)
\]

or their sampled approximations.

For smooth Euclidean examples the profile rapidly stabilizes.

For the Heisenberg example it stabilizes to the anisotropic Carnot geometry.

Later candidates:

- a cone point;
- a tree;
- a self-similar ultrametric;
- a sampled surface;
- a singular algebraic variety with a separately chosen dilation model.

Do not claim a dilation structure merely because a picture has a zoom animation; the coherence axioms are extra structure.

## Experiment 4: decorated crossing evaluator

Represent \(x\circ_\varepsilon y\) as a decorated crossing.

Allow the same expression to be viewed in three synchronized forms:

1. algebraic tree;
2. decorated tangle/port graph;
3. evaluated points in a chosen model.

Start with Euclidean semantics and Heisenberg semantics.

This is the most direct way to make "computing with space" testable rather than metaphorical.

## Experiment 5: Reidemeister law checker

Given a selected algebraic structure, enable only the diagram moves justified by its laws.

Possible modes:

- plain idempotent right quasigroup;
- distributive irq / quandle-like mode;
- concrete Euclidean emergent algebra;
- concrete Heisenberg emergent algebra.

A move that is visually familiar but algebraically invalid should fail loudly.

This would be useful outside this repository because knot-diagram software often treats Reidemeister moves as purely topological and forgets that decorations impose algebraic conditions.

## Experiment 6: approximate-operation compiler

Input:

\[
\Sigma^x_\varepsilon(u,v),\quad
\Delta^x_\varepsilon(u,v),\quad
\mathrm{inv}^x_\varepsilon(u).
\]

Compile each expression into the primitive dilation/undilation graph.

Then:

- simplify symbolically when the model permits it;
- evaluate numerically;
- animate the graph as \(\varepsilon\to0\).

This is a small but real compiler from derived geometry into primitive local operations.

## Experiment 7: graph-rewrite microscope

Use one generic port-graph renderer and load several rewrite systems:

- graphic lambda calculus;
- chemlambda v2;
- zipper logic;
- directed interaction combinators.

At each step show **all** currently matching local rewrites, not only the one chosen by the scheduler.

For a random scheduler, record:

- chosen rewrite;
- competing matches;
- node/edge counts;
- connected components;
- hash/canonical label for small graphs;
- whether a previous isomorphism class has reappeared.

This makes quines and rewrite conflicts visible.

## Experiment 8: quine recurrence viewer

For known small chemlambda quines, render a state graph whose vertices are graph-isomorphism classes and whose edges are rewrites.

For tiny molecules this can be exhaustive rather than sampled.

Questions:

- Is recurrence a single cycle or a larger strongly connected component?
- Which scheduler choices leave the recurrent set?
- Where do multiplication/death branches split off?
- Which statistics are actually invariant?

## Experiment 9: Euclidean vs Heisenberg same syntax

Take one decorated-crossing expression and evaluate it in both models.

The syntax remains identical; the semantics differ.

This is probably the cleanest demonstration of why the primitive should be "dilation operation on points" rather than "vector arithmetic."

## Experiment 10: typed API sketch

The point type should remain opaque.

\`\`\`
interface Scale scale where
  one      : scale
  multiply : scale -> scale -> scale
  inverse  : scale -> scale

interface DilationSpace point scale where
  dilate   : point -> scale -> point -> point
  undilate : point -> scale -> point -> point
\`\`\`

The laws include:

\`\`\`
dilate x e x = x
dilate x one y = y
dilate x e (dilate x f y) = dilate x (multiply e f) y
undilate x e (dilate x e y) = y
\`\`\`

Derived finite-scale operations:

\`\`\`
differenceAt x e u v =
  undilate (dilate x e u) e (dilate x e v)

sumAt x e u v =
  undilate x e (dilate (dilate x e u) e v)

inverseAt x e u =
  undilate (dilate x e u) e x
\`\`\`

A tangent structure should be a different object, indexed by its base point:

\`\`\`
TangentAt space x
\`\`\`

Only there should group addition/inverse and scalar dilation be exposed.

The actual convergence proofs cannot be represented by pretending a floating-point threshold *is* a limit. Numerical tests are evidence for examples, not the definition of the mathematical structure.

## Rendering note

Nothing here requires a heavy engine. The geometry needs:

- 2-D/3-D points and lines;
- camera transforms;
- graph layout;
- text labels;
- frame capture.

The mathematical data structures should be independent of Sokol/raylib/Android rendering. That keeps this work reusable by the singularity, knot/Kirby, tessellation, and permutation visualizers.
