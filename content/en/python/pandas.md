---
title: Pandas
---

## Links
- indexing and selecting data: <https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html>
- using iloc, loc, & ix: <https://www.shanelynn.ie/select-pandas-dataframe-rows-and-columns-using-iloc-loc-and-ix/>
- iterating dataframes
  - iterrows: <https://pandas.pydata.org/pandas-docs/version/0.17.0/generated/pandas.DataFrame.iterrows.html>
  - itertuples: <https://pandas.pydata.org/pandas-docs/version/0.17.0/generated/pandas.DataFrame.itertuples.html>
  - iteritems: <https://pandas.pydata.org/pandas-docs/version/0.17.0/generated/pandas.DataFrame.iteritems.html>


## Create Dataframe
```python
data = {"col1": [1, 2], "col2": [3, 4]}
df = pd.DataFrame(data=data)
```

## Load and Save CSV
- save to CSV: `df.to_csv("path_or_buffer.csv")`
- save to CSV (without row names / index): `df.to_csv("path_or_buffer.csv", index=False)`
- save to compressed CSV (without row names / index): `df.to_csv("path_or_buffer.csv.gz", compression="gzip", index=False)`
- load from CSV:
```python
df = pd.read_csv(
    "path_or_buffer",
    sep=";",
    encoding="us-ascii",
    usecols=col_list,
    nrows=number_of_rows_to_read,
    low_memory=False,
    quoting=csv.QUOTE_NONE,
)
```
- load csv without header: `df = pd.read_csv("path_or_buffer", names=["column_name_1", "column_name_2"], header=None)`

## Load and Save CSV Parquet
- save to parquet: `df.to_parquet("<file_name>.parquet.gz", compression="gzip")`
- load from parquet: `df = read_parquet("<file_name>.parquet.gz")`

## Display Data
- count values in column (without `NaN` values): `df["col_name"].value_counts()`
- count values in column (with `NaN` values): `df["col_name"].value_counts(dropna=False)`
- duplicates
  - display duplicate rows: `df[df.duplicated(keep=False)]`
  - display duplicate entries in column: `df[df["column_name"].duplicated(keep=False)]`

## Delete Data
- delete column inline
  - `df.drop("column_name", axis=1, inplace=True)`
  - `column_name` can also be a list of `str`
- remove rows on condition: `df.drop(df[df["col_name"] == condition].index, inplace=True)`
- remove duplicates
  - keep first (inplace): `df.drop_duplicates(inplace=True, keep="first")`
  - only consider certain columns to identify duplicates, keep first (inplace): `df.drop_duplicates(list_of_cols, inplace=True, keep="first")`

## Modify Data
- sort
  - low to high values: `df.sort_values("column_name", inplace=True)`
  - high to low values: `df.sort_values("column_name", ascending=False, inplace=True)`
  - high to low values & `Nan` values on top: `df.sort_values("column_name", ascending=False, na_position="first")`
- shuffle: `df = df.sample(frac=1).reset_index(drop=True)`

## Combine Data

### Stack two Dataframes
Never forget to `ignore_index` or you have duplicate index values and
bad things might happen later!
```python
df = pd.concat([df_01, df_02], ignore_index=True)
```

## Display Settings
Examples for display settings:
```python
pd.set_option("display.max_rows", None)
pd.set_option("display.max_columns", None)

# display long sentences in multiple rows (Jupyter)
pd.set_option("display.max_colwidth", None)
```

## Filter nan Values
`nan == nan` is always `false`. That is why we can not use `==` to
check for `nan`-values. Use `pd.isnull(obj : scalar or array-like)`
instead or `isnull()`. Examples:
```python
df.loc[pd.isnull(df["col"])]
df[df["col"].isnull()]
```

## Other
- rename columns: `df.rename(columns={"a": "x"}, inplace=True)`
