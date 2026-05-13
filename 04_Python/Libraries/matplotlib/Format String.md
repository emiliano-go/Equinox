A format string consists of a part for color, marker and line:

```python
fmt = '[marker][line][color]'
```

Each of them is optional. If not provided, the value from the style cycle is used. Exception: If `line` is given, but no `marker`, the data will be a line without markers.

**Markers**

| character | description           |
| --------- | --------------------- |
| `'.'`     | point marker          |
| `','`     | pixel marker          |
| `'o'`     | circle marker         |
| `'v'`     | triangle_down marker  |
| `'^'`     | triangle_up marker    |
| `'<'`     | triangle_left marker  |
| `'>'`     | triangle_right marker |
| `'1'`     | tri_down marker       |
| `'2'`     | tri_up marker         |
| `'3'`     | tri_left marker       |
| `'4'`     | tri_right marker      |
| `'8'`     | octagon marker        |
| `'s'`     | square marker         |
| `'p'`     | pentagon marker       |
| `'P'`     | plus (filled) marker  |
| `'*'`     | star marker           |
| `'h'`     | hexagon1 marker       |
| `'H'`     | hexagon2 marker       |
| `'+'`     | plus marker           |
| `'x'`     | x marker              |
| `'X'`     | x (filled) marker     |
| `'D'`     | diamond marker        |
| `'d'`     | thin_diamond marker   |
| `'\|'`    | vline marker          |
| `'_'`     | hline marker          |

**Line Styles**

|character|description|
|---|---|
|`'-'`|solid line style|
|`'--'`|dashed line style|
|`'-.'`|dash-dot line style|
|`':'`|dotted line style|

Example format strings:
```python
'b'    # blue markers with default shape
'or'   # red circles
'-g'   # green solid line
'--'   # dashed line with default color
'^k:'  # black triangle_up markers connected by a dotted line
```

**Colors**

The supported color abbreviations are the single letter codes

|character|color|
|---|---|
|`'b'`|blue|
|`'g'`|green|
|`'r'`|red|
|`'c'`|cyan|
|`'m'`|magenta|
|`'y'`|yellow|
|`'k'`|black|
|`'w'`|white|

and the `'CN'` colors that index into the default property cycle.

If the color is the only part of the format string, you can additionally use any [`matplotlib.colors`](https://matplotlib.org/stable/api/colors_api.html#module-matplotlib.colors "matplotlib.colors") spec, e.g. full names (`'green'`) or hex strings (`'#008000'`).