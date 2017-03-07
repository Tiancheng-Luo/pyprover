# PyProver

PyProver is a resolution theorem prover for first-order predicate logic. PyProver is written in [Coconut](http://coconut-lang.org/) which compiles to pure, universal Python, and allowing PyProver to work on any Python version.

Installing PyProver is as simple as
```
pip install pyprover
```

## PyProver Basics

To use PyProver from an interpreter, it is recommended to
```python
from pyprover import *
```
which will populate the global namespace with capital letters as propositions/predicates, and lowercase letters as constants/variables/functions.

Formulas can be constructed using the built-in Python operators on propositions and terms combined with `Exists` (or `TE`), `ForAll` (or `FA`), `top`, and `bot`. For example:
```python
A & B
A | ~B
~(A | B)
P >> Q
P >> (Q >> P)
(F & G) >> H
E >> top
bot >> E
FA(x, F(x))
TE(x, F(x) | G(x))
FA(x, F(f(x)) >> F(x))
```

Once a formula has been constructed, various functions are provided to work with them. Some of the most important of these are:

- `strict_simplify(expr)` finds an equivalent, standardized version of the given `expr`,
- `simplify(expr)` is the same as `strict_simplify`, but it implicitly assumes `TE(x, top)`,
- `strict_proves(givens, concl)` determines if `concl` can be derived from `givens`, and
- `proves(givens, concl)` is the same as `strict_proves`, but it implicitly assumes `TE(x, top)`.

To construct additional propositions/predicates, the function `propositions("name1 name2 name3 ...")` will return propositions/predicates for the given names, and to construct additional constants/variables/functions, the function `terms("name1 name2 name3 ...")` can be used similarly.
