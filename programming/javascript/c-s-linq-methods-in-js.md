---
description: 'JavaScript equivalents of C# LINQ methods.'
---

# C\#'s LINQ methods in JS

| C\# LINQ Method | JavaScript Array Method |
| :--- | :--- |
| `.Where(i => i == 1)` | `.filter(i => i === 1)` |
| `.Select(i => i.Name)` | `.map(i => i.name)` |
| `.Aggregate()` | `.reduce((item1, item2) => item1.length + item2.length)` |
| `.Any()` | `.some(i => i.id > 100)` |
| `.All()` | `.every(i => i.id > 100)` |
| `.OrderBy()` | `.sort((a,b) => { return a.name > b.name ? 1 : 0 })` |
|  |  |

