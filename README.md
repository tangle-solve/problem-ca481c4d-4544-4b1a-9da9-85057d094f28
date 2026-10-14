<!-- solve-problem:ca481c4d-4544-4b1a-9da9-85057d094f28 -->
# Barendregt–Geuvers–Klop conjecture

A [Tangle Solve problem](https://solve.tangle.tools/problems/ca481c4d-4544-4b1a-9da9-85057d094f28).

## What is the problem?

A **pure type system (PTS)** is specified by a triple (S, A, R) of sorts, axioms, and rules; its terms are generated from variables, application, and typed abstraction (λx:A. t) with typing and β-reduction defined in the standard way (Barendregt's cube and beyond). Reduction is confluent for all PTSs. The conjecture asks:

**If every well-typed term of a PTS is weakly normalizing (WN: some reduction sequence reaches a normal form), must the system be strongly normalizing (SN: all reduction sequences terminate)?**

Equivalently: can there exist a PTS in which every typable term *has* a normal form reachable by a clever strategy, yet some typable term admits an infinite reduction sequence? The conjecture asserts this cannot happen: **WN ⟹ SN for pure type systems**. Note the claim is about *pure* type systems — no Σ-types, definitions, or general rewriting added; extensions with such features are known to admit counterexamples, so the restriction is essential.

## Why does it matter?

PTSs are the unifying framework for the λ-cube (simply typed λ-calculus, System F, Fω, LF, the Calculus of Constructions), so the conjecture says weak normalization results would automatically yield strong normalization — decidable type checking with an arbitrary strategy, and semantic consistency via normalization, come for free. It also probes a deep mystery: WN is typically proved semantically (models) while SN is proved syntactically (reducibility candidates); a positive answer would tie these together. Proof assistants and logical frameworks whose kernels rely on termination properties would gain simpler correctness arguments.

## What's already known?

- The full conjecture is open. It is attributed to Barendregt, and appears via Geuvers' work (hence "Barendregt–Geuvers–Klop" in some listings).
- The converse (SN ⟹ WN) is trivial.
- Positive results for restricted classes: the implication holds for the systems of the λ-cube; Geuvers–Nederhof gave a modular SN proof for a class including the Calculus of Constructions; Melliès–Werner gave a generic reducibility-candidate SN proof covering PTSs satisfying certain (stronger than WN) hypotheses. Sørensen and others verified the conjecture for various syntactically constrained classes (e.g., singly-sorted / sort-structured systems) — details of exactly which classes are settled should be **verified** against the literature before relying on them.
- Crucially, known *failure* phenomena guide intuition: with Σ-types, definitions, or β-reduction combined with η or user-defined rewriting, WN without SN is achievable (e.g., via self-application-like loops that are still "rescuable" by a strategy). The open question is whether the bare PTS discipline (β only) rules this out.
- A natural attack: classify PTSs by their (S, A, R) — since a PTS's strength is essentially determined by which of R's rule pairs {(s1,s2,s2)} it contains (the "PTS sort graph"). One seeks a combinatorial/proof-theoretic analysis of which sort graphs allow non-SN terms that are nonetheless weakly normalizing.

## What would count as solving it?

1. **Positive resolution:** a proof that for every PTS (S, A, R), WN implies SN; a referee would demand it handle all pathological rule sets, not just the λ-cube shapes.
2. **Negative resolution:** an explicit PTS (S, A, R) and a well-typed term that is weakly normalizing (a reduction to normal form must be exhibited) yet has an infinite reduction sequence.
3. **Partial results count as progress:** proof of the implication for an infinite, previously open family of PTSs (e.g., all non-dependent or all "functional"/singly-sorted systems), or a characterization of the obstruction in the general case.

## How to start

1. Read Barendregt's "Lambda calculi with types" (Handbook of Logic in Computer Science, 1992), §5.2–5.5, for the PTS framework and the normalization-spectrum definitions (WN, SN, and the logical relations between them).
2. Read Geuvers' 1993 thesis and Geuvers–Nederhof (1991) to see which system shapes have settled SN, and Melliès–Werner (1998) for the strongest generic reducibility machinery — the main technical toolkit for any positive attack.
3. Attempt the contrapositive: assume WN + ¬SN and study the shape of minimal non-SN typable terms in a PTS (often self-application (λx. x x)(λx. x x)-style terms typable only with dependent sorts). Check whether the typing discipline of an arbitrary sort graph forbids WN counterexamples.
4. Main obstacle: WN gives no inductive handle — there is no known measure or reducibility-style interpretation that extracts SN from a mere existence-of-normal-forms property; standard candidates (Tait/Girard) require strictly more than WN.

## Key references

- H. Barendregt, "Lambda calculi with types," in Handbook of Logic in Computer Science, Vol. 2, OUP, 1992. — The standard reference defining PTSs, the λ-cube, and the normalization hierarchy; source of the conjecture's framing. (No stable URL; widely available in print/online.)
- H. Geuvers, "Logics and Type Systems," PhD thesis, Radboud University Nijmegen, 1993. — Studies normalization for PTSs, including modular proofs; closest source document for the conjecture's attribution (verify exact statement location).
- H. Geuvers and M.-J. Nederhof, "Modular proof of strong normalization for the calculus of constructions," Journal of Functional Programming 1(2), 1991. — Proves SN for a broad class of PTSs via translation to Fω-style systems.
- P.-A. Melliès and B. Werner, "A generic normalization proof for pure type systems," in TYPES '96, LNCS 1512. — Girard-style reducibility-candidate proof of SN under general hypotheses — the strongest general SN technique available.
- Wikipedia, "List of unsolved problems in computer science." — The census source listing the problem as open (2026-10-07): https://en.wikipedia.org/wiki/List_of_unsolved_problems_in_computer_science

## Warnings

- Do not "solve" this by adding Σ-types, η, or rewriting and exhibiting a counterexample — counterexamples in those extensions are known and irrelevant; the conjecture is strictly about pure β-reduction PTSs.
- The attribution ("Klop") is uncertain in the census; the conjecture is usually cited as Barendregt's, sometimes Barendregt–Geuvers — verify attribution before publishing.
- Be careful with the definitions: WN here means every *typable* term is weakly normalizing; untyped-λ-calculus intuition (where WN ⊬ SN trivially) does not transfer.
- The terms "normalizing" vs "strongly normalizing" vary across literature — always check which is meant in any cited result before citing it as a partial solution.

---
*`ALGO-000223` · unverified*

## Acceptance guidance

1. **Positive resolution:** a proof that for every PTS (S, A, R), WN implies SN; a referee would demand it handle all pathological rule sets, not just the λ-cube shapes.
2. **Negative resolution:** an explicit PTS (S, A, R) and a well-typed term that is weakly normalizing (a reduction to normal form must be exhibited) yet has an infinite reduction sequence.
3. **Partial results count as progress:** proof of the implication for an infinite, previously open family of PTSs (e.g., all non-dependent or all "functional"/singly-sorted systems), or a characterization of the obstruction in the general case.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/ca481c4d-4544-4b1a-9da9-85057d094f28?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000223.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000223)
