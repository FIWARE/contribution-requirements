## Configuring webhook in a FIWARE GitHub repository

In order to connect your repository with the mirror webhook you simply have to
follow these steps:

-   In your repository page, click **Settings**.

![](img/01-repo-settings.jpeg)

-   Once you are in the Settings page, click on **Webhooks** menu and then in
    the button **Add webhook**.

![](img/02-add-webhook.jpeg)

-   Fill in the form:

    -   **Payload URL** - `https://webhook.fiware.org/mirror`
    -   **Content type** - `application/json`
    -   **SSL verification** - **Enable SSL verification**
    -   **Events** - **Send me everything**

![](img/03-configure-webhook.jpeg)

-   Open webhook

![](img/041-check-webhook.jpeg)

-   Check status code and reply

![](img/042-check-webhook.jpeg)
