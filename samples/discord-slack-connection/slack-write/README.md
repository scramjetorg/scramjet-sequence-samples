# Slack Write

Read messages from topic and write to slack.

In order to get SLACK_WEBHOOK_URL you need to create application in Slack first.
Please refer to notes in [slack-read](../slack-read/) example.

Once you have a application in Slack. Open it and under Features select `Incoming Webhooks`

Activate incoming webhooks and add a new webhook to workspace by clicking on `Add New Webhook to Workspace` button. Follow prompts and select which channel you want to use.

Copy Webhook URL and use it later as `SLACK_WEBHOOK_URL` in the notes below.

## Running

```bash
# install dependencies
npm install

# transpile TS->JS to dist/
npm run build

# prepare standalone JS package
cp -r node_modules package.json dist/

# make a compressed package with sequence
si pack dist

# send sequence to transform hub, this will output Sequence ID
si seq send dist.tar.gz

# start a sequence, this will output Instance ID. Provide SLACK_WEBHOOK_URL as the second parameter
si seq start <sequence-id> <SLACK_WEBHOOK_URL>

# view messages in topic
si topic get messages

```