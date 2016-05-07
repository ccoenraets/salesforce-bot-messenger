## Salesforce Bot for Facebook Messenger

A simple Salesforce bot for Facebook Messenger.

See [this blog post](http://coenraets.org/blog/2016/04/salesforce-bot-for-facebook-messenger/) for details.

### Create a Connected App


### Deploy the Messenger Bot

1. Make sure you are logged in to the [Heroku Dashboard](https://dashboard.heroku.com/)
1. Click the button below to deploy the Messenger bot on Heroku:

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

- Enter the client id and client secret for your connected app
- Enter the user name and password for your integration user
- For VERIFY_TOKEN, enter a passphrase of your choice. You'll have to enter the same passphrase when you create the webhook in Facebook.
- Leave PAGE_TOKEN blank for now


### Create a Facebook App

1. Follow [these instructions](https://developers.facebook.com/docs/messenger-platform/quickstart) to create a Facebook app.

    - When asked for a Callback URL, enter the URL of the Heroku app you just deployed followed by /webhook. For example:
        ```
        https://myapp.herokuapp.com/webhook
        ```
    - When asked for the Verify Token, enter the passphrase you entered when you deployed the Heoku app
    - When the page access token is generated, login to the Heroku Dashboard, and set the Heroku PAGE_TOKEN config variable to the value of that token.           
    - Don't forget the "Subscribe the App to the Page" step.

        ```
        curl -ik -X POST "https://graph.facebook.com/v2.6/me/subscribed_apps?access_token=<token>"
        ```
    - You don't need to implement the Receive Messages step as the webhook is already implemented in the Heroku app.
    
1. In Messenger, search for your bot in the search box, type Help to see what you can ask, and start chatting with your bot!
