# Expanding the toolbox for OBIS users

This repository will be used to hold the discussions about developing new tools for OBIS data processing and analysis, as part of the [OBIS products infrastructure](https://github.com/iobis/obis-hub). This will involve:

1. Identify currently available functions (`obistools` package, but also other functions and packages created by the OBIS secretariat and nodes)
2. Verify improvement needs in those existing tools
3. Identify existing gaps and propose new tools

We decided to create a new repository, instead of holding the discussions on the `obistools` package repo, to enable a clean view over the topic. Depending on the outcomes we can then decide to implement those tools on the existing package or develop a complimentary package.

The idea is also that we will be able to create a "language-agnostic"[^1] package, in the sense that we will have functions for multiple languages using the same or very similar syntaxes.

For example, the current `obistools` function `check_onland()` that is used on R as:

```r
abra <- arrow::read_parquet("abra_occurrences.parquet")

report <- check_onland(abra, report = TRUE, buffer = 100)

print(report)
```

Could be similarly used in Python:

```python
import pandas as pd

abra = pd.read_parquet("abra_occurrences.parquet")

report = check_onland(abra, report=True, buffer=100)

print(report)
```

And on Julia:

```julia
using Arrow

abra = Arrow.read_parquet("abra_occurrences.parquet") |> DataFrame

report = check_onland(abra, report=true, buffer=100)

println(report)
```

[^1]: Note that a true language-agnostic, or cross-platform, package would mean that it is written in such a way that it can be used or integrated into different programming languages without modification. In our case, what is more probable is that we will have functions written in partially distinct ways according to each language, but with the same arguments and outputs.
