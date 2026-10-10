# What seems mathematically important, and what is speculative?

## Strongest mathematical core

### 1. Dilation structures

This is a serious intrinsic-geometry program: use coherent local dilations on metric spaces to recover tangent objects and differential calculus.

The sub-Riemannian case is the convincing example because ordinary tangent vector spaces are the wrong local algebra; Carnot groups appear naturally.

Primary sources:

- https://arxiv.org/abs/math/0608536
- https://arxiv.org/abs/0708.4298
- https://arxiv.org/abs/0810.5042
- https://arxiv.org/abs/1206.3093

### 2. Emergent algebras

The algebraic extraction is, in my view, the cleanest idea in the corpus: a very weak-looking scale-indexed quasigroup structure can generate approximate difference/sum/inverse and, after limits, a tangent group.

It also explains why the subject touches knot theory: racks/quandles live immediately next door.

Primary source:

https://arxiv.org/abs/0907.1520

### 3. Diagrammatic bridge

Using decorated crossings as syntax for emergent-algebra operations is mathematically natural once the irq/quandle relation is present.

Graphic lambda calculus then gives a genuine formal object connecting those diagrams with lambda-calculus graphs.

Primary sources:

- https://arxiv.org/abs/1009.5028
- https://arxiv.org/abs/1305.5786

### 4. Local graph rewriting

Chemlambda, zipper logic, and related systems are explicit graph-rewrite systems. Whatever one thinks of the surrounding "chemistry" metaphor, the rewrite dynamics are concrete and implementable.

Primary sources:

- https://arxiv.org/abs/1405.6095
- https://arxiv.org/abs/2007.10288
- https://arxiv.org/abs/2003.14332

## More speculative layers

### Front-end visual system

Buliga has proposed that emergent-algebra/diagrammatic computation is relevant to the way early vision reconstructs space.

That is an interesting research analogy, not an established result in neuroscience. The repository should not phrase it as one.

### Artificial chemistry / artificial life interpretation

Quines, replication-like graph behavior, conflicting local reactions, and asynchronous schedules are real properties of the formal systems.

Calling those phenomena "life" or treating the rewrite chemistry as a model of physical chemistry is a further interpretive step.

### Molecular computers

The proposal to implement graph rewriting in actual molecular chemistry is a separate engineering/scientific program. It should not be used as evidence for the mathematical claims about the rewrite system itself.

## My working judgment

The part most worth stealing intellectually is not the rhetoric around "space computing." It is this more precise pattern:

1. choose extremely local primitive operations;
2. refuse to assume the global algebra you ultimately want;
3. compose the local operations at finite scale;
4. identify the laws that hold before taking a limit;
5. take a controlled limit or repeated-rewrite regime;
6. see which larger algebra/semantics emerges.

That pattern fits several of the other repositories unusually well.

For geometry it says: do not start by vectorizing everything.

For graph computation it says: do not start by installing a global evaluator into every node.

For knot/tangle diagrams it says: encode exactly which algebraic law makes a move legal.

Those are reusable design principles even if none of the stronger biological claims is pursued.
