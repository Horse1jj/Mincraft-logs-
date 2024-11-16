# Mincraft-logs-

This script is designed to log Minecraft events to local files and send them to webhooks for external integration (e.g., Discord, APIs). It's flexible and easily configurable through a config.json file.

## Features

Event Logging: Tracks the following events:
Player chat messages

Block breaks and placements
Player joins and quits

Webhook Integration: Sends event logs to specified webhook URLs.

Local File Logging: Saves logs in categorized and date-stamped files.

Scheduled Cleanup: Automatically deletes logs older than 7 days (optional).

Folder Structure

minecraft-server/
├── plugins/
│   ├── Denizen/
│   │   ├── scripts/
│   │   │   ├── advanced_logger.dscript   # Main script
│   │   │   ├── config.json               # Configuration for webhook URLs
│   │   │   ├── logs/                     # Folder for log files (auto-created)
│   │   │   └── README.md                 # This file

## Setup Instructions

**1. Install Denizen**

Ensure Denizen is installed on your Minecraft server.

Download it from https://denizenscript.com/.

**2. Add the Script**

Place advanced_logger.dscript in the plugins/Denizen/scripts/ folder.

**3. Configure Webhooks**

Create a config.json file in the same folder as the script with the following structure:

``` json 
{
  "webhooks": {
    "chat": "https://example.com/webhook/chat",
    "block_break": "https://example.com/webhook/block_break",
    "block_place": "https://example.com/webhook/block_place",
    "join": "https://example.com/webhook/join",
    "quit": "https://example.com/webhook/quit"
  }
}

```

Replace the URLs with your actual webhook endpoints (e.g., Discord webhooks).

**4. Reload Scripts**

Run /denizen reload scripts in the server console or in-game to activate the script.
How It Works

**Local File Logging**

Logs are stored in the logs/ folder with filenames like ```chat_YYYY-MM-DD.log.```
Example log entry:

```[10:45:32] Player123: Hello world!```

**Webhook Logging**

Sends log entries as JSON payloads to the configured webhook URL.

Example payload for a chat message:

``` bash
{
  "content": "[10:45:32] Player123: Hello world!"
}

```


## Customization

**Events to Log**

Add or remove events in the advanced_logger.dscript file under the events section.

**Log Cleanup**

By default, logs older than 7 days are deleted.

Modify the cleanup_old_logs task in the script to adjust this behavior.

**Debugging**

To enable debugging, set debug: true in the script or task definitions.

## Testing

Trigger Events:

Chat in-game, break/place blocks, or join/quit the server.

**Verify Logs:** 

Check the logs/ folder for the corresponding log file.

**Check Webhooks:**

Ensure your webhook endpoint receives the events.

**Troubleshooting**


No Logs are Being Created
Check for errors in the Denizen debug console (/denizen debug).

Verify file permissions for the scripts/ folder.

**Webhook Data Not Sent**

Verify the webhook URL in config.json is correct.

Use a service like Webhook.site to debug incoming requests.

## Credits

Script created for Minecraft servers using Denizen.

Documentation and setup guide by foste1jj, lead dev @ CR design studio.
