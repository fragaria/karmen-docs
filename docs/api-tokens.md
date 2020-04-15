# API tokens

Sometimes, you need to access the application automatically — for example to run
a monitoring dashboard or to access the API programatically. For that, Karmen
offers API tokens tied to a certain user account and organization. Everyone can
create as many tokens as they want. The API tokens have the following
properties:

- They never expire.
- They are always in the *user* role, so you cannot use them for adding printers
  for example.
- They are bound to a single organization.
- They can be revoked from the application.

!> The tokens are signed by the application and if you change the
``KARMEN_SECRET_KEY`` value in your configuration, they will stop working
altogether.

You can create new API token in your account settings (click on your account in the app menu).

<div class="center">

![API token list](_media/api-tokens.png ":size=600x131")

</div>

Click on the **Add token** button, name your new API token and select
organization for which it should be available.

<div class="center">

![New API token](_media/new-api-token.png ":size=600x335")

</div>

## Running a monitoring dashboard {docsify-ignore}

For the monitoring dashboard use case, you can run the UI in your browser
directly with the token like this:

```bash
http://<karmen-address>/?token=<my-api-token>
```


If you need to automate some administrative tasks, you should be successful if
you copy your active session token (after you are prompted for password) from a
browser's session cookies. Such token will expire in a few minutes, though, so
you have to be quick.
