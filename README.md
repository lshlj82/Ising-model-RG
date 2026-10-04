# The renormalization group for the Ising model

An interactive, single-file web demo of real-space renormalization for the Ising model: Kadanoff's block spins, exact decimation in one dimension, truncated decimation in two dimensions, and Wilson's flow in coupling space. It is based on lecture notes by Sang Hoon Lee for Chapter 2, which follow K. Christensen and N. R. Moloney, *Complexity and Criticality* (2005). It completes the series of percolation and Ising demos.

Everything runs in the browser. There is no build step, no server and no dependencies beyond an optional web font. Units are k<sub>B</sub> = 1 and J = 1.

## Running it

Open `index.html` in any modern browser (Chrome, Edge, Firefox or Safari).

To publish it with GitHub Pages, push this repository, then go to **Settings → Pages**, choose **Deploy from a branch**, and select the branch and the root folder. The page will be served at `https://<user>.github.io/<repository>/`.

## What the page contains

**Live block-spin transformation.** Three lattices are simulated live at t &lt; 0, t = 0 and t &gt; 0, updating once every 0.1 s. Each is coarse-grained twice with b = 3 (243 → 81 → 27) or b = 2 (256 → 128 → 64), using the majority or decimation rule, as in Fig. 2.32 of the notes. A chart tracks the nearest-neighbor correlation of block spins over three RG steps: it flows toward 1 below T<sub>c</sub>, toward 0 above, and changes least at T<sub>c</sub>.

**Kadanoff's block spins.**

- the three-step procedure and the coarse-graining rules
- the derivation of t′ = b<sup>y<sub>t</sub></sup>t and h′ = b<sup>y<sub>h</sub></sup>h with y<sub>t</sub> = 1/ν, the invariance of Z, and f(t, h) = b<sup>−d</sup>f(b<sup>y<sub>t</sub></sup>t, b<sup>y<sub>h</sub></sup>h), which yields Widom's ansatz
- a calculator that gives ν, α, β, γ, δ, η and Δ from y<sub>t</sub>, y<sub>h</sub> and d, with presets for the 2D Ising model, the 3D Ising model and mean field at d = 4

**Exact renormalization in one dimension.**

- decimation with b = 2: K<sub>1</sub>′ = ½ ln cosh 2K<sub>1</sub> and K<sub>0</sub>′ = ln[2√(cosh 2K<sub>1</sub>)]
- a cobweb plot of the flow to the stable fixed point K* = 0 from the unstable one at ∞
- a table showing ξ halving exactly at each step
- a check that the summed offsets reproduce the exact free energy ln(2 cosh K)

**Decimation in two dimensions.**

- the generated couplings K<sub>1</sub>′, K<sub>2</sub>′ and K<sub>3</sub>′, illustrated on the lattice before and after decimation
- two truncations: dropping all new couplings (no transition, which is wrong), and K̃′ = ⅜ ln cosh 4K̃, which has a non-trivial fixed point K̃* ≈ 0.507 and gives ν ≈ 0.93 from the slope there

**Wilson's renormalization group.**

- coupling space, fixed points with ξ = 0 or ∞, basins of attraction and the critical surface
- linearization near the fixed point, with relevant, irrelevant and marginal scaling fields
- a clickable flow diagram of the two-coupling approximation K′ = 2K² + L, L′ = K², with its critical line, the eigen-directions and eigenvalues at (1/3, 1/9) (ν ≈ 0.64), and K<sub>c</sub> ≈ 0.392 on the original model's axis
- how the RG reproduces Widom's scaling form and explains universality

## Methods

| Topic | Approach |
| --- | --- |
| Block-spin lattices | Metropolis single-spin updates only: 3 000 sweeps at T = T<sub>c</sub>(1 + t) at full speed to equilibrate, then one sweep every 0.1 s; correlations averaged after equilibration |
| Coarse-graining | Majority of the b × b block (random tie-breaking for b = 2) or its top-left spin |
| 1D free energy | ln Z/N = Σ<sub>n</sub> K<sub>0</sub><sup>(n)</sup>/2<sup>n</sup> along the flow |
| 2D fixed point | Bisection on K̃′ − K̃; ν = ln b / ln λ with b = √2 |
| Two-coupling flow | Exact iteration of K′ = 2K² + L, L′ = K²; the critical line by bisection on the fate of each starting point |

## Files

```
index.html   the complete demo (HTML, CSS and JavaScript in one file)
README.md    this file
```

## References

**Key reference.** K. Christensen and N. R. Moloney, *Complexity and Criticality*, Imperial College Press, London (2005), Chapter 2.

1. L. P. Kadanoff, "Scaling laws for Ising models near T<sub>c</sub>," *Physics* **2**, 263 (1966).
2. K. G. Wilson, "Renormalization group and critical phenomena. I. Renormalization group and the Kadanoff scaling picture," *Phys. Rev. B* **4**, 3174 (1971).
3. K. G. Wilson, "Renormalization group and critical phenomena. II. Phase-space cell analysis of critical behavior," *Phys. Rev. B* **4**, 3184 (1971).
4. H. J. Maris and L. P. Kadanoff, "Teaching the renormalization group," *Am. J. Phys.* **46**, 652 (1978).
5. N. Goldenfeld, *Lectures on Phase Transitions and the Renormalization Group*, Addison-Wesley (1992).
6. J. Cardy, *Scaling and Renormalization in Statistical Physics*, Cambridge University Press (1996).

## Credits

Lecture notes: Sang Hoon Lee.

Created by Claude Opus 5.5.
