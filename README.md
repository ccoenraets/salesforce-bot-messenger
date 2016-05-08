## Salesforce Bot for Facebook Messenger

A simple Salesforce bot for Facebook Messenger.

See [this blog post](http://coenraets.org/blog/2016/04/salesforce-bot-for-facebook-messenger/) for details.

### Create a Connected App

1. In Setup, enter **Apps** in the quick find box, and click the Apps link

1. In the **Connected Apps** section, click **New**, and define the Connected App as follows:

    - Connected App Name: MyConnectedApp
    - API Name: MyConnectedApp
    - Contact Email: enter your email address
    - Enabled OAuth Settings: Checked
    - Callback URL: http://localhost:8200/oauthcallback.html (You'll change this later)
    - Selected OAuth Scopes: Full Access (full)
    - Click **Save**

### Deploy the Messenger Bot

1. Make sure you are logged in to the [Heroku Dashboard](https://dashboard.heroku.com/)
1. Click the button below to deploy the Messenger bot on Heroku:

    [![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

1. Fill in the config variables as described.

    - Leave **FB_PAGE_TOKEN** blank for now
    - For **FB_VERIFY_TOKEN**, enter a passphrase of your choice. You'll have to enter the same passphrase when you create the webhook in Facebook.
    - For **SF_CLIENT_ID**, enter the Consumer Key of your Salesforce Connected App
    - For **SF_CLIENT_SECRET**, enter the Consumer Secret of your Salesforce Connected App
    - For **SF_USER_NAME**, enter the the username of your Salesforce integration user
    - For **SF_PASSWORD**, enter the the username of your Salesforce integration user

### Create a Facebook App

1. Follow [these instructions](https://developers.facebook.com/docs/messenger-platform/quickstart) to create a Facebook app. You'll have to create a Facebook page, a Facebook application, and configure Messenger for your application.

    - When asked for a **Callback URL**, enter the URL of the Heroku app you just deployed followed by /webhook. For example:
        ```
        https://myapp.herokuapp.com/webhook
        ```
    - When the Page Access Token is generated, login to the Heroku Dashboard, and set the Heroku **FB_PAGE_TOKEN** config variable to the value of that token (**Setting>Reveal Config Vars**)
    - When asked for the **Verify Token**, enter the value you entered for the **FB_VERIFY_TOKEN** config variable when you deployed the Heroku app.
    - Make sure you select a page in the **Select a page to subscribe your webhook...** dropdown
    
1. Visit the Facebook page you created in the previous step, and click the **Message** button. Type **help** in the chat bot. You can continue the conversation with the bot in the Messenger app on your phone or in the browser (http://messenger.com).
