# telescoping

Notes and experiments around the work of **Marius Buliga**, especially the line

[
	ext{coherent dilation/zoom} longrightarrow
	ext{emergent algebra} longrightarrow
	ext{diagrammatic local computation}.
]

The repository name is descriptive rather than Buliga's terminology: the recurring move is to compare a space at nested scales and ask what algebraic structure stabilizes as the scale tends to zero.

## Core idea

In Euclidean space a dilation based at (x) is

[
delta^x_arepsilon(y)=x+arepsilon(y-x).
]

Buliga's dilation structures ask how much of differential geometry survives if coherent families of such "zoom" operations are taken as primitive, without assuming a vector space or smooth manifold in advance.

At small scales, approximate difference, sum, and inverse operations can converge to genuine algebraic operations on tangent objects. The tangent is generally not forced to be a vector space: in sub-Riemannian examples it is naturally a **conical/Carnot-type group**, so noncommutative addition is expected rather than pathological.

The algebraic abstraction is an **emergent algebra**: a scale-indexed family of idempotent right-quasigroup operations. Group-like and differential structure is derived from repeated dilation operations and limiting behavior rather than installed at the start.

## Why this is interesting

This gives a route between several subjects that are usually presented separately:

- metric and sub-Riemannian geometry;
- tangent cones and Carnot groups;
- affine geometry without a primitive vector-space structure;
- quandles, braids, and Reidemeister-style diagrammatics;
- lambda calculus and local graph rewriting;
- chemlambda / artificial-chemistry experiments.

The surprising part is not merely that these topics coexist in one body of work. The **same local-operation viewpoint** keeps reappearing.

## Reading path

1. **Dilatation structures I. Fundamentals** — the basic geometric machine.
2. **Introduction to metric spaces with dilations** — shorter entry point.
3. **Emergent algebras** — isolates the algebra underneath the geometry.
4. **What is a space?** — decorated crossings and a visual/computational interpretation.
5. **λ-Scale** — mixes lambda calculus with scaled/dilation operations.
6. **Graphic lambda calculus** — graph language covering lambda calculus, emergent-algebra computation, and tangle/Reidemeister structure.
7. **Zipper logic** and **chemlambda** — increasingly local graph-rewrite systems and artificial-chemistry experiments.

See `notes/roadmap.md` for the detailed map.

## Questions for this repository

- Can one make the emergence of tangent algebra literally visible under continuous zoom?
- Which dilation-structure axioms admit useful finite tests on sampled metric spaces?
- Can approximate sum/difference/inverse be implemented independently of coordinates?
- What is the cleanest typed representation of an emergent algebra?
- How much of the decorated-crossing calculus can be shared with knot/Kirby-diagram tooling?
- Can one put metric dilation rewrites and lambda/chemlambda rewrites in one small graph-rewrite engine without pretending they are the same semantics?
- Which examples genuinely need noncommutative tangent groups, with the Heisenberg group as the first test case?

## Credit

These notes are about and rely heavily on Marius Buliga's work. Primary sources should be cited directly in any derived implementation or exposition. The bibliography in this repository favors his arXiv papers and author-maintained project pages.
