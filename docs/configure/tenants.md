# Tenants

This is where you'll see and manage the tenants of your workspace.

--8<-- "reusables/tenant-callout.md"

![Tenants from admin dashboard](/assets/images/admin-tenants.png)

## Base URL

Each tenant is tied to a **base URL**: each routes, like login or registration, will be derived from this base. When you integrate Fief in your application, you'll need this base URL.

Each workspace has **one default tenant** with a base URL pointing to your root subdomain, like *https://example.fief.dev*.

Other tenants gets a path prefix, like *https://example.fief.dev/other-tenant*.

!!! tip
    You can copy the base URL directly using the clipboard button in the list.


## Create a new tenant

You can create a new tenant by clicking the **Create Tenant** button. A modal will open where you'll be able to input:

* Its name.
* If [user registration is allowed](#disable-user-registration).

The [base URL](#base-url) is automatically generated from the name.

Optionally, you can also set:

* A logo URL that will be shown on the top-left of authentication pages.
* A [UI theme](./customization/themes.md) to use when users authenticate with this tenant. If left empty, the theme set as default is used.
* The list of [OAuth Providers](./oauth-providers.md) allowed to be used on this tenant.

![Create tenant from admin dashboard](/assets/images/admin-tenants-create.png)

## Edit an existing tenant

If you click on one of the tenant in the list, you'll see its details on the right.

![View tenant details from admin dashboard](/assets/images/admin-tenants-view.png)

If you click on the **Edit Tenant** button, you'll be able to update its properties.

![Edit tenant from admin dashboard](/assets/images/admin-tenants-edit.png)

## Disable user registration

You can choose to **disable user registration** on a tenant. To do this, you have to uncheck the **Registration allowed** checkbox in the tenant details.

When registration is disabled, users can't access the registration page and create a new account on this tenant.

## Delete a tenant

If one your tenant is not useful anymore, you can delete it by clicking on it on the list and click on the **Delete** button on the right.

![Delete tenant from admin dashboard](/assets/images/admin-tenants-delete.png)

!!! danger "Users and clients will be removed as well"
    When you delete a tenant, all its associated users and clients will be deleted as well. The data won't be recoverable. Be sure of what you're doing!

## Transactional emails

Quite often, Fief needs to **send emails to your users**, like **welcome email** or **forgot password** emails. The layout and content of those emails can be customized, as explained in the [Email templates](./customization/email-templates.md) section.

Of course, those emails need to be sent by a specific email address and name, the **From** part of an email. By default, they will be sent by the address defined globally on the Fief server, i.e. `Fief <contact@fief.dev>` on Fief Cloud. This may not be user-friendly for your users and it'll probably better to send emails from an email address you own matching your brand.

Fortunately, you can customize this in the **Email** tab of a tenant. Fill the **From name** and **From email** with a valid name and email address and click on **Update**.

![Tenant transactional emails settings from admin dashboard](/assets/images/admin-tenants-email.png)

### Domain authentication

To allow the Fief server to send emails on your behalf, you need to **authenticate your email domain**. For this, you'll have to set some DNS records on your domain registrar.

Click on **Manage domain authentication** to see the list of DNS records you need to set. Once done, click on the **Verify** button to validate that you correctly set the DNS records.

![Tenant transactional emails domain authentication](/assets/images/admin-tenants-email-domain-authentication.png)

!!! tip "Note for self-hosted servers"
    If you self-host your Fief server, please note that only the [SendGrid provider](../self-hosting/deployment/setup-email-provider.md#postmark-provider) supports domain authentication from the admin dashboard. If you use SMTP or Postmark, you should manually authenticate your domain.
