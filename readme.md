## testing

This is to test providing an auth-admin app for sql-based security, using
1. `ui/admin/admin_loader.py` as provided by Thomas,
2. `api/expose_api_models.py` to expose auth models (which breaks BLT, btw)


Established security:
```bash
als add-auth --provider-type=sql
```

It works for:
1. sql auth-admin at: http://127.0.0.1:5656/01/auth-admin/index.html
2. " " as docker app


## Issues

### Fails when switch to KC
But, it fails if you switch to Keycloak:
```bash
als add-auth --provider-type=keycloak
```

### Expose_models breaks BLT (multi-database test)

Even tried to make it conditional:

```python
    """"
    try:  # sql auth provider - manage users/roles at: http:/localhost:5656/01/auth-admin/index.html#/Home
        provider_name = Args.instance.security_provider.__dict__['__module__']
        if Args.instance.security_enabled and 'security.authentication_provider.sql.auth_provider' == provider_name:
            for name, obj in inspect.getmembers(database.database_discovery.authentication_models):
                if inspect.isclass(obj) and issubclass(obj, database.models.SAFRSBaseX) and obj is not database.models.SAFRSBaseX:
                    app_logger.info(f"Exposing /{name}")
                    api.expose_object(add_check_sum(obj), method_decorators= method_decorators)
    except Exception as e:
        app_logger.warning(f"api/expose_api_models unable to expose sql authentication models: {e}")
    """
```


## ToDo

Try as a docker app.
