Azure Automation Two-Way Slack Integration [Webhook]
====================================================

            
Introduction

This Azure Automation Runbook demonstrates how to run PowerShell code inside an Azure Automation Runbook, in response to a
[Slack](https://en.wikipedia.org/wiki/Slack_Technologies) integration command. The PowerShell script Runbook in Azure Automation also responds by sending an outgoing (from Azure Automation's perspective) webhook call. The outbound webhook call sends
 a message to a Slack channel.


This Runbook was developed by [Trevor Sullivan](https://trevorsullivan.net), a multi-awardee of the Microsoft MVP award for
[Windows PowerShell](https://msdn.microsoft.com/powershell) automation. You can find Trevor on
[Twitter @pcgeek86](https://twitter.com/pcgeek86).


In order to utilize this Runbook, you'll import it into your Microsoft Azure Automation Account from the
[Runbook Gallery](https://azure.microsoft.com/en-us/documentation/articles/automation-runbook-gallery/). After you've imported the Runbook, go through the steps below to configure it.

Step 1. Create a Webhook

This Runbook is already set up to receive Webhook data, via the **$WebhookData** parameter, however you must create a
[Webhook in Azure Automation](https://azure.microsoft.com/en-us/documentation/articles/automation-webhooks/) to enable remote invocation of the Runbook (from Slack, in this case). After importing this Runbook, open the Runbook's blade, and click on Webhooks. Follow the directions from there.

Step 2. Set up a Slack Integration Command

In order to call this Runbook from Slack, you'll set up a [custom slash command](https://my.slack.com/services/new/slash-commands). You can choose whichever command name you want to, but in my case, I chose
**/runbook**. In the **URL** field, you'll copy / paste the webhook URL for the Runbook, that you generated in Step #1. The
**Method** field should be set to POST, because [Azure Automation expects a HTTP POST message](https://azure.microsoft.com/en-us/documentation/articles/automation-webhooks/). All of the other settings are optional.


You can optionally specify a custom name for the webhook, under the **Customize Name** field.

Step 3. (Optional) Set up a Slack Incoming Webhook

If you want the Azure Automation Runbook to send messages back to one of your Slack channels, you'll need to set up a
[Slack incoming webhook](https://my.slack.com/services/new/incoming-webhook/). Once this has been completed on the Slack side, created a
**Variable Asset** in your Azure Automation Account named 
**SlackIncomingWebhook**, and copy / paste the value of the Slack Incoming Webhook URL into this variable's value field. The Runbook will look for this variable, to send messages from Azure Automation, over to your Slack channel. 


 

 

        
    
TechNet gallery is retiring! This script was migrated from TechNet script center to GitHub by Microsoft Azure Automation product group. All the Script Center fields like Rating, RatingCount and DownloadCount have been carried over to Github as-is for the migrated scripts only. Note : The Script Center fields will not be applicable for the new repositories created in Github & hence those fields will not show up for new Github repositories.
