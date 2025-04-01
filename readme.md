## testing

This is to test providing an auth-admin app for sql-based security, using `ui/admin/admin_loader.py` as provided by Thomas.


Established security:
```bash
als add-auth --provider-type=sql
```

T
for
1. sql auth-admin at: http://127.0.0.1:5656/01/auth-admin/index.html
2. " " as docker app

But, it fails if you switch to Keycloak:
```bash
als add-auth --provider-type=keycloak
```

TODO: try as a docker app.
