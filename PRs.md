

# TODO
- replace datetime.now() with timezone.now()
- test against versions of Postgres 12, 13, 14, 15, 16 https://hub.docker.com/_/postgres/ with setup and teardown.
- `/.venv/lib/python3.11/site-packages/setuptools/installer.py:27: SetuptoolsDeprecationWarning: setuptools.installer is deprecated. Requirements should be satisfied by a PEP 517 installer.`
- WARNING: The `wheel` package is not available.
- `[pbr] Generating ChangeLog /media/led/hdd/repos/capone/.venv/lib/python3.11/site-packages/setuptools/command/easy_install.py:146: EasyInstallDeprecationWarning: easy_install command is deprecated. Use build and pip and other standards-based tools.`
- `/media/led/hdd/repos/capone/.venv/lib/python3.11/site-packages/setuptools/command/install.py:34: SetuptoolsDeprecationWarning: setup.py install is deprecated. Use build and pip and other standards-based tools.`

# django 5 feature branch
- Drop support for Django < 4.2 (3.2 LTS EOL [is end Q1 2024](https://endoflife.date/django))
- Drop support for Python < 3.8
- Removed `enum34`, as it is a backport of the Python 3.4 enum module and is unnecessary in Python 3.6+
- Relaxed upper version constraints on other requirements
- updated `tox.ini` to reflect version changes
- Remove Django Python 2 [compatibility APIs](https://docs.djangoproject.com/en/3.2/releases/3.0/#removed-private-python-2-compatibility-apis) 
- `django.utils.translation` [switched to](https://docs.djangoproject.com/en/3.2/releases/3.0/#id3) `gettext_lazy`
- Adjusted `Makefile` to use python3 `venv` module instead of `virtualenv`
- Upgrade `pip` when creating a virtual environment.
- Update `settings.py`
  - Modernize `MIDDLEWARE` declaration, including `SecurityMiddleware`, `CsrfViewMiddleware`, `XFrameOptionsMiddleware`
  - Add `DEFAULT_AUTO_FIELD`
  - Add `TEMPLATES` declaration
  - Add `django.contrib.messages` to `INSTALLED_APPS`
- `setup.cfg`
  - updated keys from kebab to snake case
  - Removed old Python versions from classifiers, simplified to Python 3

- `capone.models.Transaction.validate()` returns `True` if no primary key is set
- Factory Boy: import `DjangoModelFactory` from `factory.django` 

## Parameeterize feature branch
- Added support for control over variables using `.env` environment file, included `.env.example` file.
- Adopted official Postgres environment variable names https://www.postgresql.org/docs/current/libpq-envars.html
- Docker compose file to provide Postgres instance for testing
- parameterized settings for database creation and management:
  - `capone_test_db` >> `PGDATABASE`
  - Add password to Postgres Django user `PGPASSWORD`

  ## docs feature branch
  - Created plant UML class diagram
  - Moved Capone mugshot and class diagram to `docs/` directory

  ## .gitignore feature branch
  - Updated `.gitignore`