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

But, it fails if you switch to Keycloak:
```bash
als add-auth --provider-type=keycloak
```

TODO: try as a docker app.
