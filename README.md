## Welcome to SpinAuthenticator - User Authentication for hubspot.

### Discussion

HubSpot is a great platform for all your contact information and a great way to interact. But to provide your customers integrated and secure access to pages that need authentication, you'll need another solution.

With SpinAuthenticator you can integrate client-side authentication on hubspot using just a minimal lightweight Javascript library.<br>

To add this library to your site, add:

```markdown
<script type='text/javascript' src='https://cdn.rawgit.com/rahulasati/hub-auth/master/js/1.0.0/spinauth.min.js'></script>
```

### Usage

We have developed this library to solve authentication problem for hubspot but if you're looking for simple client side authentication apart from hubspot so definitely it will probably meet your needs.

This javascript library is intentionally small and minimalistic.

### By using SpinAuthenticator you can achieve:

1. Provide users with secure access to HubSpot pages.
2. Easy customer registration service on HubSpot landing pages.
3. Simple Login flow with email and password.
4. Remembers the login until explicitly logged out by user. 


### Limitation:

1. Social Login is not supported for now.
2. Not integrated with HubSpot CRM (User Management).


### Add Authetication to page

Add following piece of code on page we want to secure with a call to HA.init(options)

```markdown
<script type="text/javascript">
        window.onload = function () {
            HA.init({
                API_KEY: 'xxxxx-xxxxx-xxxxx-xxxxx',
                AUTH_PAGE_URL: '/url/--/auth.html',
                complete: function (err, message) {
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

**API_KEY** – an application's unique key, please contact us at support@spinfluence.co<br>

**AUTH_PAGE_URL** – The Authentication page, in case of auth fail we will redirect user to this page.<br>

**complete** – a function(err, data) that will be called when initialization is complete.<br>

### User Registeration

```markdown
<script type="text/javascript">
        HA.performRegister({
            API_KEY: 'xxxxx-xxxxx-xxxxx-xxxxx',
            first_name: '',
            last_name: '',
            email: '',
            password: '',
            complete: function (err, message) {
                if (err) {
                    // if error then registeration fails take action based on message.
                } else {
                    // registration successfull, verification email has been send once that is done proceed with login.
                    // here disply message received in callback data field and go to login.
                }
            }
        });
</script>
```

These all fields are required:

**API_KEY** – an application's unique key, please contact us at support@spinfluence.co<br>
    
**first_name** – first name of the user. <br>

**last_name** – last name of the user. <br>

**email** – email address of the user. <br>

**password** – password.<br>

**complete** – a function(err, data) that will be called when registration is complete.<br>


### User Login

```markdown
    <script type="text/javascript">
        HA.performLogin({
            API_KEY: 'xxxxx-xxxxx-xxxxx-xxxxx',
            email: '',
            password: '',
            complete: function (err, user) {
                if (err) {
                    // if error then attempt to login failed, display reason of failuare using err.
                    // here remain on login screen only.
                } else {
                    // login successful redirect to main screen.
                }
            }
        });
    </script>
```
**API_KEY** – an application's unique key, please contact us at support@spinfluence.co<br>

**email** – email.<br>

**password** – password.<br>

**complete** – a function(err, data) that will be called when login is complete.<br>


### User Logout
    
```markdown
<script type="text/javascript">
    HA.logout({
        API_KEY: 'xxxxx-xxxxx-xxxxx-xxxxx',
        AUTH_PAGE_URL: '/url/--/auth.html',
    });
</script>
```
**AUTH_PAGE_URL** – After logout, it will be redirected to specified page url.<br>


### Resend Email Verification (if required)

```markdown
<script type="text/javascript">
    HA.resendVerificationMail({
        API_KEY: 'xxxxx-xxxxx-xxxxx-xxxxx',
        email: '',
        complete: function (err, message) {
            if (err) {
                // error while sending verification email, check error.
            } else {
                // verification email has been sent successfully, check your email.
            }
        }
    });
</script>
```
**API_KEY** – an application's unique key, please contact us at support@spinfluence.co<br>

**email** – email address of the user for which email verification is pending.<br>

**complete** – a function(err, data) that will be called when registration is complete.<br>

