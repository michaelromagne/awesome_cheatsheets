# (WIP) Python cheatsheets


## Pyenv + Poetry

Pyenv & Poetry save my projects.

https://blog.jayway.com/2019/12/28/pyenv-poetry-saviours-in-the-python-chaos/

## Pytest

Pytest is awesome to unit test your code.

I especially love the coverage report feature. You can generate reports to see where your code has not been tested. 
Of course it is only an indicator and 100% coverage does not mean at all that your code is well tested. You should think of edge cases before.
But it's still nice to have this indicator :
```
pytest --cov-report html --cov=omni_ai tests/
```
