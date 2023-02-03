# (WIP) Data Analysis

<p align="center">
  <img src="/img/python.png" width=150 />
</p>

Maybe I should put my favorite viz or data analysis commands somewhere to stop harassing stackoverflow or scrolling documentations for the very same questions.

## Pandas

- Display all rows of a pandas DataFrame for ad-hoc analysis:
```
with pd.option_context('display.max_rows', None, 'display.max_columns', 10):
  display(df)
```

- Put color in your life with Styler:
```
# Define colormap
def color_negative_red(val):
    """
    Takes a scalar and returns a string with
    the css property `'color: red'` for negative
    strings, black otherwise.
    """
    color = 'red' if np.abs(val) > 0.1 else 'black'
    return 'color: %s' % color

s = df.style.applymap(color_negative_red)

```

- Sort DataFrame rows by a column following a specific key function in descending order:
```
df.sort_values(by='sorting_col', key=abs, ascending=False)
```

## Seaborn as sns

- Seaborn [displot](https://seaborn.pydata.org/generated/seaborn.displot.html) is neat to vizualize distributions in different format. It can also do kernel density estimations that can be great for some use cases:
```
sns.displot(data=merge_df_cg, x="x_col", hue="group", kind="kde",....)
```

## explainerdashboard

I like the [explainerdashboard package](https://explainerdashboard.readthedocs.io/en/latest/) for its flexibility and how it's quick to use. If you want to dig a bit in your model decision without having the time to design a proper dashboard, it's pretty sure that they have a minimal solution for you ready in one of their dashboards.

```
from explainerdashboard import ClassifierExplainer, ExplainerDashboard

explainer = ClassifierExplainer(model, X, y)
ExplainerDashboard(
    explainer,
    decision_trees=False, # You can disable some of their widgets
    mode='external', # Nice to continue to play in your notebook
).run(port=8050) # Make sure the port is available
```

