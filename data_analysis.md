# (WIP) Data Analysis

<p align="center">
  <img src="/img/python.png" width=300 />
</p>

Maybe I should put my favorite viz or data analysis commands somewhere to stop harassing stackoverflow or scrolling documentations for the very same questions.

## Pandas

- Display all rows of a pandas DataFrame for ad-hoc analysis:
```
with pd.option_context('display.max_rows', None, 'display.max_columns', 10):
  display(df)
```