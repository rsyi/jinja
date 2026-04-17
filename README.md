# jinja2

A Jinja2-compatible template engine for Rust with full feature parity, built on [minijinja](https://github.com/mitsuhiko/minijinja).

## Installation

```sh
cargo add jinja2
```

## Quick start

```rust
use jinja2::{new_jinja2, context};

let mut env = new_jinja2();
env.add_template("hello", "Hello {{ name|upper }}!").unwrap();
let tmpl = env.get_template("hello").unwrap();
let result = tmpl.render(context!(name => "world")).unwrap();
assert_eq!(result, "Hello WORLD!");
```

`new_jinja2()` returns a `minijinja::Environment` pre-loaded with every Jinja2 built-in. You can also call `add_jinja2_compat(&mut env)` on an existing environment.

## What's included

Everything in [minijinja](https://github.com/mitsuhiko/minijinja) (all features enabled), plus the gaps filled for full Jinja2 parity:

**All 51 Jinja2 filters** — `abs`, `attr`, `batch`, `capitalize`, `center`, `default`/`d`, `dictsort`, `escape`/`e`, `filesizeformat`, `first`, `float`, `forceescape`, `format`, `groupby`, `indent`, `int`, `items`, `join`, `last`, `length`/`count`, `list`, `lower`, `map`, `max`, `min`, `pprint`, `random`, `reject`, `rejectattr`, `replace`, `reverse`, `round`, `safe`, `select`, `selectattr`, `slice`, `sort`, `string`, `striptags`, `sum`, `title`, `tojson`, `trim`, `truncate`, `unique`, `upper`, `urlencode`, `urlize`, `wordcount`, `wordwrap`, `xmlattr`

**All 33 Jinja2 tests** — `boolean`, `callable`, `defined`, `divisibleby`, `eq`/`equalto`/`==`, `escaped`, `even`, `false`, `filter`, `float`, `ge`/`>=`, `gt`/`greaterthan`/`>`, `in`, `integer`/`int`, `iterable`, `le`/`<=`, `lower`, `lt`/`lessthan`/`<`, `mapping`, `ne`/`!=`, `none`, `number`, `odd`, `sameas`, `sequence`, `startingwith`, `endingwith`, `string`, `test`, `true`, `undefined`, `upper`

**All 7 Jinja2 global functions** — `range`, `dict`, `debug`, `namespace`, `cycler`, `joiner`, `lipsum`

**All 17 Jinja2 tags** — `for` (with `else`, `recursive`, filtered), `if`/`elif`/`else`, `extends` (dynamic), `block` (with `super()`), `include` (with `ignore missing`), `import`, `from...import`, `macro`, `call`, `set` (incl. block form), `with`, `filter`, `do`, `autoescape`, `raw`, `break`, `continue`

**Full Python method compatibility** — `str.upper()`, `str.lower()`, `str.strip()`, `str.replace()`, `str.split()`, `str.startswith()`, `str.endswith()`, `str.center()`, `str.ljust()`, `str.rjust()`, `str.zfill()`, `dict.items()`, `dict.keys()`, `dict.values()`, `dict.get()`, `list.append()`, `list.extend()`, `list.pop()`, and more

**Bonus** — `as_bool` filter, `chain`/`zip`/`lines`/`bool`/`split` filters, `pluralize` filter, `randrange` function

## License

Apache-2.0
