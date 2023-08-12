Panama TSE
===

Where to place external-check?
---
Inside `app/ext_check.py`

How to develop locally?
---
We use [Poetry](https://python-poetry.org/) for local development. Consider [installing](https://python-poetry.org/docs/#installation) it.

After that you need to create [Gitlab access token](https://gitlab.mati.io/-/profile/personal_access_tokens) with `read_api`, `read_registry` and `read_repository` scopes.

Then add your access credentials and registry with:
```bash
$ poetry config repositories.legal-checks https://gitlab.mati.io/api/v4/projects/323/packages/pypi/
$ poetry config http-basic.legal-checks <access_token_name> <access_token_value>
```
***Note***: you should do this step only *ONCE*

And finally, you can install all required dependecies:
```bash
$ poetry install
```

How to run service locally?
---
you need to set environment variables. an example can be taken from the deploy configs or the `pytest.ini` file

command to run rmq consumer:
```bash
$ python -m app.worker
```

command to run http server:
```bash
$ python -m uvicorn app.api:app
```

Deploy to env instruction:
---
[Gitlab link](https://gitlab.mati.io/legal-checks/legal-apps)