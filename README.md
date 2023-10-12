# checkmoddep

🚧🚨 **UNDER CONSTRUCTION**
This is a *draft* for an idea. Nothing actually working to been seen here, yet.

## Idea

When developing projects according to some architectural guidelines, then you
often want to separate code of different architectural layers into different
modules.

It is important to get all people working on the project to adhere to these
ideas, but it would make contributions easier if we could enforce these
architectural guidelines in CI, just like a linter validates for coding
standards, I would like to see an architectural linter.

This module is an attempt at this to check and enforce that a module `a` (e.g. the
domain layer) does not depend on `b` (e.g. the persistence layer). Therefore if
`a.py` contains `import b`, we want to raise an error.

## Draft

Since this is some kind of test, we would ideally integrate with an existing
testing framework like `pytest`.

A test might look like:

```python
from checkmoddep import depends_on, assert_depends_on, assert_not_depends_on
import domain_layer
import persistence_layer

def test_a_does_not_depend_on_b():
    assert_not_depends_on(domain_layer, persistence_layer)
```

## Previous work

Noteworthy work that is related to what `checkmoddep` will achieve:

- [pydeps](https://github.com/thebjorn/pydeps), used for visualizing dependencies
- [modulegraph](https://github.com/ronaldoussoren/modulegraph)
- [modulegraph2](https://github.com/ronaldoussoren/modulegraph2)
- [import-deps](https://github.com/schettino72/import-deps), using `ast` to analyze a set of specified modules. Last commit Jan 2022. No test suite.
- [snakefood](https://github.com/blais/snakefood), Python 2 only, uses `ast` - for visualization and checking unused modules.
- [only-relative-import](https://github.com/Kludex/only-relative-import), can enforce relative only imports
