Postgres audit database via triggers
====================================

This app sets up a postgres audit database via triggers.
See https://wiki.postgresql.org/wiki/Audit_trigger_91plus
and https://github.com/2ndQuadrant/audit-trigger/
for more information.


Installation
============
`pip install postgres_audit_triggers`


Usage
=====

- Add the `audit` app to `INSTALLED_APPS` *before* any apps that will be audited:

```
# settings.py
INSTALLED_APPS = {
    'audit.apps.AuditConfig',
    ...
}
```

- Add `audit_trigger = True` to the Model Meta options of the models that will be audited:

```
# models.py
class MyAuditedModel(models.Model):
    ...
    class Meta:
        audit_trigger = True
        ...
```

- Make migrations: `python manage.py makemigrations`
- Run migrations: `python manage.py migrate`
