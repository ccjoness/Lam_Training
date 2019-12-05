Django does a few things to ensure that projects are secure. You can read the full details in the [Django Documentation on Security](https://docs.djangoproject.com/en/2.1/topics/security/): 


## Cross site request forgery (CSRF) protection
CSRF attacks allow a malicious user to execute actions using the credentials of another user without that user’s knowledge or consent.

Django has built-in protection against most types of CSRF attacks, providing you have enabled and used it where appropriate. However, as with any mitigation technique, there are limitations. For example, it is possible to disable the CSRF module globally or for particular views. You should only do this if you know what you are doing. There are other limitations if your site has subdomains that are outside of your control.

CSRF protection works by checking for a secret in each POST request. This ensures that a malicious user cannot simply “replay” a form POST to your website and have another logged in user unwittingly submit that form. The malicious user would have to know the secret, which is user specific (using a cookie).

When deployed with HTTPS, CsrfViewMiddleware will check that the HTTP referer header is set to a URL on the same origin (including subdomain and port). Because HTTPS provides additional security, it is imperative to ensure connections use HTTPS where it is available by forwarding insecure connection requests and using HSTS for supported browsers.

Be very careful with marking views with the csrf_exempt decorator unless it is absolutely necessary.

## SQL injection protection
SQL injection is a type of attack where a malicious user is able to execute arbitrary SQL code on a database. This can result in records being deleted or data leakage.

Django’s querysets are protected from SQL injection since their queries are constructed using query parameterization. A query’s SQL code is defined separately from the query’s parameters. Since parameters may be user-provided and therefore unsafe, they are escaped by the underlying database driver.

Django also gives developers power to write raw queries or execute custom sql. These capabilities should be used sparingly and you should always be careful to properly escape any parameters that the user can control. In addition, you should exercise caution when using extra() and RawSQL.
## Clickjacking protection
Clickjacking is a type of attack where a malicious site wraps another site in a frame. This attack can result in an unsuspecting user being tricked into performing unintended actions on the target site.

Django contains clickjacking protection in the form of the X-Frame-Options middleware which in a supporting browser can prevent a site from being rendered inside a frame. It is possible to disable the protection on a per view basis or to configure the exact header value sent.

The middleware is strongly recommended for any site that does not need to have its pages wrapped in a frame by third party sites, or only needs to allow that for a small section of the site.

## Lam Security measures
There are a few things that we are doing to make sure the Gemini project is secure internally.

- You must be connected and authenticated on LAM's secure network to access Gemini source code.
- You must have elevated access to BitBucket and be authenticated on LAM's secure network to make any changes to Gemini's source code.
- If a script is modified and ran, a warning is logged with the time, date, and user that is logged in.
