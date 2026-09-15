# Discrete-Time Markov Chains

Lecture notes on discrete-time Markov chains, written in LaTeX and compiled to an
18-page PDF. Covers the chain from its definition through classification of states,
recurrence and transience, and the conditions under which a limiting distribution exists.

Transition diagrams are drawn in TikZ rather than pasted as images, so every figure is
editable in the source.

📄 **[DTMC.pdf](DTMC.pdf)** — the compiled notes
📝 **[main.tex](main.tex)** — LaTeX source

---

## Contents

### Discrete-Time Markov Chains

The setup and the basic machinery.

- **The Markov property** — the future is conditionally independent of the past given the
  present, framed against the two extremes of i.i.d. variables and full dependence on
  history.
- **Definition and time-homogeneity** — when one-step probabilities don't depend on $n$,
  and the two conditions that make $P$ a stochastic matrix: entries in $[0,1]$ and rows
  summing to 1.
- **Initial distribution and characterization** — why $P$ alone isn't enough to pin down
  the chain, worked through a joint probability, and why the pair $(P, \mathbf{a})$ is.
- **Four examples, each with a transition diagram** — a two-state up/down machine; two
  independent machines, where the state is the number currently up and the entries follow
  from independence; brand switching among three beers; and gambler's ruin on
  $\{0, 1, \dots, N\}$ with its two absorbing states and transient interior.

### Transient behavior

$n$-step transition probabilities, the Chapman–Kolmogorov equation, and
$P^{(n)} = P^n$ in the time-homogeneous case. A four-state example computes a joint
probability along a specific path, marginalizes over the initial state, and iterates the
marginal distribution forward.

### Limiting behavior

The motivating question: does $\lim_{n\to\infty} \mathbf{a}^{(n)}$ exist, and does it
depend on where the chain started?

Two contrasting examples answer both halves. In the brand-switching chain the rows of
$P^n$ converge to a common vector, so the limit exists and the initial distribution
washes out. In a second chain $P^n$ alternates between two matrices depending on the
parity of $n$, so no limit exists and the answer stays tied to $\mathbf{a}$. This sets up
the two properties that matter: **periodicity** and **irreducibility**.

### Classification of states

- **Accessibility and communication** — $i \to j$, $i \leftrightarrow j$, and the
  transitivity theorem.
- **Communicating classes**, closed vs. open, and the fact that once the chain enters a
  closed class it never leaves.
- **Irreducibility** — one closed communicating class containing everything.
- **Periodicity** — the period as the gcd of return times, aperiodicity when $d = 1$, and
  the theorem that all states in a communicating class share a period. Worked through
  examples including a chain whose three classes have different periods.

### Recurrence and transience

- A side-by-side table contrasting the two: whether you return infinitely often, whether
  the expected number of visits is finite, and whether the return probability $f_i$
  equals 1.
- **First passage time** $T_i = \min\{n > 0 : X_n = i\}$ and the definition of $f_i$.
- **Intuition** — the number of visits is geometric for a transient state, giving
  $E[N \mid X_0 = i] = 1/(1 - f_i)$.
- **The characterization** $\sum_n P_{ii}^{(n)} = \infty$ iff $i$ is recurrent, with a
  proof sketch using indicator variables.
- **Class properties** — recurrence and transience are class properties, and in a finite
  state space every closed class is recurrent while every open class is transient.

### Limiting behavior of irreducible chains

Three theorems for finite state spaces:

1. A finite irreducible chain has a unique stationary distribution $\pi$ with
   $\pi P = \pi$, summing to 1, with all entries strictly positive.
2. **Ergodic theorem** — if the chain is also aperiodic, $P_{ij}^{(n)} \to \pi_j$, and
   $\pi_j$ is the long-run fraction of time spent in state $j$.
3. If the chain is periodic, the limiting probability fails to exist, but the stationary
   distribution still does.

Closing examples: brand switching converging to $\pi = [0.132, 0.319, 0.549]$; a
two-state chain with period 2 and no limiting distribution; and an irreducible aperiodic
two-state chain converging to $[0.462, 0.538]$.

---

## Building from source

A single-file `article` with no external figures — all diagrams are TikZ, so it compiles
anywhere with a standard TeX distribution:

```bash
pdflatex main.tex
```

Packages used: `amsmath`, `amssymb`, `amsthm`, `bm`, `graphicx`, `geometry`, `array`, and
`tikz` with the `automata`, `arrows`, `arrows.meta`, and `positioning` libraries.

---

## A note on scope

These are one student's lecture notes, written to be readable later rather than to be
comprehensive. Corrections are welcome by issue or pull request.
