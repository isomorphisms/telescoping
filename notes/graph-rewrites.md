# From decorated crossings to chemlambda

## 1. Why the computation work belongs in the same repository

The graph-rewrite work is not simply a later hobby disconnected from the dilation work.

The chain is explicit in Buliga's papers:

\[
\text{dilations}
\to
\text{emergent algebra}
\to
\text{decorated tangle diagrams}
\to
\lambda\text{-Scale}
\to
\text{graphic lambda calculus}
\to
\text{chemlambda / zipper logic / directed interaction combinators}.
\]

The common theme is to replace global semantic machinery by compositions of small local operations.

## 2. Decorated crossings

For an emergent algebra, a crossing can carry a scale label \(\varepsilon\). The crossing represents the operation

\[
x\circ_\varepsilon y.
\]

This is not merely pictorial notation. Algebraic identities become local diagram transformations, and the relation with racks/quandles makes Reidemeister moves relevant.

Primary sources:

- Emergent algebras: https://arxiv.org/abs/0907.1520
- What is a space?: https://arxiv.org/abs/1009.5028
- Braided spaces with dilations: https://arxiv.org/abs/1005.5031

For our purposes this is a direct bridge to any reusable tangle/knot diagram data structure.

## 3. λ-Scale

Primary source: https://arxiv.org/abs/1205.0139

\(\lambda\)-Scale is an attempt to put lambda abstraction/application and scale-indexed dilation in one calculus.

The interesting idea is not "put a real number into lambda calculus." It is that application and dilation can be combined into a scaled operation while the emergent-algebra structure remains visible.

This is the conceptual predecessor to graphic lambda calculus.

## 4. Graphic lambda calculus

Primary source: https://arxiv.org/abs/1305.5786

Graphic lambda calculus (GLC) is a class of locally planar directed graphs built from a small graphical alphabet plus graph moves.

The initial gate set includes:

- lambda-abstraction gate;
- application gate;
- fan-out gate;
- termination;
- an \(\varepsilon\)-decorated emergent-algebra gate.

The same formalism is meant to contain three sectors:

1. untyped lambda calculus;
2. emergent-algebra computations;
3. locally planar tangle/Reidemeister computations.

The graphic beta move is deliberately usable outside the lambda-calculus sector.

### Important historical limitation

GLC includes global moves/conditions and originally does **not** prescribe a local rewrite scheduler. This matters because the later chemlambda work is partly an attempt to get rid of that global machinery.

## 5. Chemlambda

Useful retrospective source:

https://arxiv.org/abs/2007.10288

Artificial-chemistry experiments:

https://arxiv.org/abs/2003.14332

Project page:

https://chemlambda.github.io/

Chemlambda turns the graph language into a more aggressively local rewrite system. Graphs are called molecules and rewrites are presented as chemical reactions.

The mature chemlambda-v2 viewpoint has:

- a finite collection of node types;
- local left-hand-side/right-hand-side rewrite patterns;
- a local rewrite algorithm;
- conflicts between simultaneously available rewrites;
- asynchronous or randomized reduction as a legitimate execution mode.

Typical node families include lambda/application, fan-in/fan-out variants, termination/free-end nodes, and temporary arrow/wire conveniences.

Typical rewrite families include beta-like, fan-in, distribution/shuffle, pruning, and wire-combination rewrites.

The exact node/rewrite inventory changes across versions, so implementations should pin a chemistry instead of saying merely "chemlambda."

## 6. Why rewrite conflicts matter

Lafont interaction combinators have a particularly clean active-port discipline. Buliga's directed interaction-combinator variant can also be arranged without rewrite conflicts.

Chemlambda v2 deliberately permits more conflicts. Buliga argues that this contributes to richer artificial-life behavior.

This gives a good experimental comparison:

- deterministic/conflict-free local interaction;
- conflict-rich local chemistry;
- same starting graph where translations exist;
- compare reduction traces, replication, termination, graph size, and recurrence.

That comparison is more informative than asking abstractly whether one formalism is "better."

## 7. Quines and artificial life

A chemlambda quine is a graph whose rewrite dynamics can return to an isomorphic graph after a nonempty collection of rewrites. Some examples also show multiplication-like and death-like behavior under random reduction.

The mathematics/computation claim is concrete: these are properties of finite graph-rewrite systems.

The stronger language of "life" is interpretive. Keep those levels separate.

Primary source:

https://arxiv.org/abs/2003.14332

## 8. Zipper logic

Primary source:

https://arxiv.org/abs/1405.6095

Zipper logic uses half-zippers, zippers, fan-in/fan-out, and termination nodes, with local moves such as CLICK, ZIP, TOWER, DIST, and pruning.

Buliga shows how:

- zipper-logic rewrites can be realized in chemlambda;
- lambda/application nodes can be represented by one-tooth half-zippers;
- SKI combinatory logic can be implemented.

The zipper representation may be particularly useful visually because an \(n\)-ary chain of local application/abstraction structure can be shown as one zipper object and then expanded.

## 9. Implementation advice for telescoping

Do **not** build "a chemlambda engine" first.

Build a neutral port-graph rewrite core:

\`\`\`
NodeType
PortType
Node
Edge
Pattern
Rewrite
Match
RewriteSchedule
\`\`\`

Then define separate chemistries:

\`\`\`
EmergentCrossings
GraphicLambda
ChemlambdaV2
ZipperLogic
DirectedIC
\`\`\`

This preserves the genuinely shared machinery without falsely identifying the systems.

Useful invariants/tests:

- port arity and orientation;
- preservation of free boundaries across a rewrite;
- no dangling references;
- deterministic canonicalization for graph-isomorphism tests on small graphs;
- exhaustive match enumeration on tiny fixtures;
- scheduler-independent invariants where the theory says they should exist.

## 10. Direct cross-links to other work

### Knot/Kirby diagram tooling

Decorated crossings are an obvious consumer of the same edge/crossing infrastructure. The rewrite semantics should remain separate from Reidemeister/Kirby semantics, but the geometric representation can be shared.

### Geometry/rendering

The emergent-algebra gate should carry a scale parameter. A renderer can therefore animate graph rewrites and geometric dilation using the same visible \(\varepsilon\).

### Typed math layer

The graph engine should not assert that a wire "is a vector." A wire carries a term/point according to the selected interpretation. Vector or tangent structure belongs to a semantics layered on top.

## 11. Questions worth pursuing

1. Can the finite-scale \(\Sigma_\varepsilon,\Delta_\varepsilon,\mathrm{inv}_\varepsilon\) expressions be compiled automatically into decorated-crossing graphs?
2. Can the same graph be evaluated in Euclidean and Heisenberg semantics?
3. Which Reidemeister moves are legal for a plain irq, and which require quandle/distributive structure?
4. Can a visualizer expose when a GLC move is local and when it depends on a global condition?
5. How much of chemlambda v2 can be expressed in a generic double-pushout-style rewrite representation without making the implementation unusably abstract?
6. Can rewrite conflicts be made visible as a branching "reaction cone" rather than hidden by one arbitrary scheduler?
