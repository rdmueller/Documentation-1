---
title: "Genesys"
slug: "genesys"
hidden: false
---
# Genesys

[![Version badge](https://img.shields.io/badge/Added in-v4.58-blue.svg)](../../release-notes/4.58.md)

<figure>
  <img class="image-center" src="{{config.site_url}}ai/handover-providers/images/genesys.svg" width="100%" />
</figure>

The **Genesys** Endpoint allows connecting virtual agent to the [Genesys Cloud CX platform](https://apps.mypurecloud.de/) using a [Genesys Bot Connector](https://help.mypurecloud.com/articles/about-genesys-bot-connector/).

## Generic Endpoint Settings

<div class="divider"></div>

Find out about the generic endpoint settings available with this endpoint on the following pages:

- [Endpoints Overview](overview.md)
- [Data Protection & Analytics](data-protection-and-analytics.md)
- [Real Time Translation Settings](real-time-translation-settings.md)
- [Transformer Functions](transformers/transformers.md)

## Channel Specific Settings

### Genesys Bot Connector Setup

| Parameter    | Description                                                                                                                                                      |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Verify Token | A verification token for connecting the Cognigy Genesys Endpoint to the Genesys Bot Connector. This token needs to be generated on the Cognigy side and can consist of letters, numbers, and punctuation marks.|

## How to Set up

To set up the Genesys Endpoint, follow these steps:

1. [Configure Genesys Endpoint](#configure-genesys-endpoint)
2. [Configure Genesys](#configure-genesys)

### Configure Genesys Endpoint

1. In the left-side menu of your Agent, click **Deploy > Endpoints**.
2. On the **Endpoints** page, click **+ New Endpoint**.
3. In the **New Endpoint** section, do the following: <br>
   3.1 Select the **Genesys** Endpoint type. <br>
   3.2 Add a unique name.<br>
   3.3 Select a relevant Flow from the list.<br>
4. In the **Configuration Information** section, copy the Endpoint URL and save it for later usage in Genesys.
5. Activate the **Enable Endpoint** setting.
6. In the **Genesys Bot Connector Setup** section, in the **Verify Token** field, create a verification token for connecting the Cognigy Genesys Endpoint to the Genesys Bot Connector. The token can consist of letters, numbers, and punctuation marks. Save this token for later usage in Genesys.
7. Click **Save**.

### Configure Genesys Cloud CX

#### Create a Genesys Bot Connector

1. Open the Genesys Cloud interface.
2. Navigate to **Admin > Integrations**.
3. Click **+ Integrations** in the upper-right corner.
4. Choose the **Genesys Bot Connector** card and click **Install**.
5. Assign a unique name to your integration.
6. On the **Configuration** tab, navigate to the **Properties** section.
7. In the **Bot Connector Handle Utterance URI** field, input the Endpoint URL value saved earlier on the Cognigy side.
8. On the **Credentials** tab, click **+Add Credentials Field**. Enter the following credentials:<br>
    - **Field Name** — use `verify-token` as the name.<br>
    - **Value** — enter the token created earlier in the **Verify Token** field on the Cognigy side.
9. Click **Ok**, then **Save**.
10. On the **Details** tab, click **Copy Integration ID** and save this ID for later use.

Your integration will be listed among integrations.

#### Add a Bot for the Bot Connector Integration

1. Open the [Genesys Developer Tools](https://developer.genesys.cloud/developer-tools/#/api-explorer) interface.
2. From the left-side menu, select **API Explorer**.
3. Navigate to **Integrations > BotConnector**.
4. Select the **PUT: Set a list of botConnector bots plus versions for this integration** option from the list.
5. Fill in the **integrationId** field with the **Integration ID** that you copied and saved earlier.
6. Within the **BODY** editor, insert the following JSON:

      ```json
      {
         "chatBots": [
            {
               "id": "<your UUID>",
               "name": "Cognigy.AI Bot",
               "versions": [
                  {
                     "version": "1",
                     "supportedLanguages": ["en-us"],
                     "intents": [
                        {
                           "name": "Success"
                        }
                     ]
                  }
               ]
            }
         ]
      }   
      ```
   The `id` field should contain your UUID, which you can create using an [online UUID generator](https://www.uuidgenerator.net/version4).<br>

7. Click **Send Request**.

#### Build an Inbound Message Flow

To create a digital bot flow in Architect, configure the inbound message flow:

1. Go to **Admin > Architect**.
2. Click or hover over the **Flows** menu and select **Inbound Message**.
3. Click **Add**. The **Create Flow** dialog box opens.
4. In the **Name** field, specify a unique name for the inbound message flow.
5. Click the **Divisions** list and select the division in which to place the flow.
6. Click **Create Flow**. The flow's configuration page opens.
7. To configure a flow, click **Edit**.
8. Go to **Toolbox**.
9. Drag the **Call bot Connector** action and drop it onto the messaging flow editor. 
10. In the right-side **Call Bot Connector** window, fill in the following fields:
    - **Bot Integration** — select the integration you created.
    - **Bot Name** — select the bot you created.
    - **Bot Version** — select the bot version you created.
11. Drag the **Send Response** action and drop it below the **Success** action. 
12. Drag the **Send Response** action and drop it below the **Failure** action.
13. In the **Message Body** of the **Send Response** actions, specify `success message` and `fail message`. 
14. Below the **Send Response** actions, place the [Transfer to ACD](https://help.mypurecloud.com/articles/transfer-acd-action/) action to transfer an interaction to a queueing system. 
15. In the **Queue** field of the **Transfer to ACD** action, select the queue to which you want to transfer the interaction.
    
    <figure>
      <img src="{{config.site_url}}ai/endpoints/images/genesys-flow-example.png" width="100%"/>
    </figure>

16. In the upper-left corner, click **Save**, then **Publish**.

After creating your inbound message flow, you will see this flow in the architect list.

To learn more about designing the flow, see [Configure Inbound Message Flow](https://help.mypurecloud.com/articles/inbound-message-flows/) settings.

#### Configure a Messenger

To create a new version of a messenger configuration and a messenger deployment, follow these steps:

1. Go to **Admin > Message > Messenger Configurations**.
2. Click **+ New Configuration**.
3. In the **Name** field, provide a unique configuration name reflecting your bot integration.
4. From the **Select your Supported Languages** list, pick available UI languages and customize text labels. Browser language determines the user's language.
5. In the **Select Default Language** field, choose a default language for cases when browser language is not detected or is not on the list.
6. Click **Save New Version**. Your configuration will appear in the configuration list.
7. Go to **Admin > Message > Messenger Deployments**.
8. Click **+ New Deployment**.
9. In the **Name** field, enter a unique deployment name that corresponds to your messenger configuration.
10. From the **Select your Configuration** list, pick the message configuration you recently created.
11. In the **Restrict domain access** section, select **Allow all domains** or specify trusted domains where Messenger can run.
12. From the **Select your Architect Flow** list, choose an existing published inbound message flow to trigger bot behavior or connect users with agents. 
13. In the **Deploy your snippet** section, click **Copy to Clipboard** to copy a code snippet onto the website pages where you would like the Messenger to appear. After deploying the snippet, any future saved changes to the configuration and deployment will be applied automatically. 
14. Click **Save**. Your deployment will then appear in the deployment list. 
15. To test the virtual agent, visit [CodeSandbox](https://codesandbox.io/) and select a default **HTML** project. Paste the copied code snippet into the `<body>` element of the HTML document.

To check the virtual agent's performance, access the installation that your server administrator has deployed.

## What's next?

Now you can configure Say, Question, and Optional Question Nodes by selecting the [Genesys](../flow-nodes/message/say.md#genesys) channel in the Node Editor settings. It's important to create messages that are compatible with the Genesys Endpoint, as the Genesys channel supports a [limited set of output types](content-conversion.md).