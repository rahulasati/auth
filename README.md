## Welcome to SpinAuthenticator - User Authentication for hubspot.

### Discussion

HubSpot is a great platform for all your contact information and a great way to interact. But to provide your customers integrated and secure access to pages that need authentication, you'll need another solution.

With SpinAuthenticator you can integrate client-side authentication on hubspot using just a minimal lightweight Javascript library.
To add this library to your site, add:

```markdown
<script type='text/javascript' src='https://cdn.rawgit.com/rahulasati/auth/master/js/1.0.0/main.js'></script>
```

### Usage

We have developed this library to solve authentication problem for hubspot but if you're looking for simple client side authentication so definitely it will probably meet your needs.

This javascript library is intentionally small and minimalistic.

### Initialization

Initialize the library prior to making any other calls with a call to HA.init(options)

```markdown
<script type="text/javascript">
        window.onload = function () {
            HA.init({
                API_KEY: 'xxxxx-xxxxx-xxxxx-xxxxx',
                authPageUrl: '/url/--/auth.html',
                complete: function (err, data) {
                    console.log('init complete callback');
                    if (err) {
                        // if error then initialization fails check for error message
                    } else {
                       // initialization successful.
                    }
                }
            });
        }
    </script>
```
These options are all required:

**API_KEY** – an application's unique key, can be created using dashboard.
**authPageUrl** – The Authentication page, in case of auth fail we will redirect user to this page.
**complete** – a function(err, data) that will be called when initialization is complete.
