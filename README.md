# Slack Bot

A feature-rich Slack bot built with Python that provides welcome messages, message counting, content moderation, and scheduled messaging capabilities.

## Features

- 🤖 **Welcome Messages**: Automatically sends interactive welcome messages to new users
- 📊 **Message Counting**: Tracks and displays user message counts
- 🛡️ **Content Moderation**: Filters and responds to inappropriate language
- ⏰ **Scheduled Messages**: Schedule messages to be sent at specific times
- 👍 **Reaction Handling**: Interactive welcome message completion tracking
- 🔗 **Slash Commands**: RESTful endpoint for message count queries

## Prerequisites

- Python 3.7+
- Slack App with appropriate permissions
- Flask web framework
- Required Python packages (see Installation)

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/prowessclust/slack-bot.git
   cd slack-bot
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables**
   Create a `.env` file in the project root:
   ```env
   SLACK_TOKEN=xoxb-your-bot-token-here
   SIGNING_SECRET=your-signing-secret-here
   ```

4. **Configure your Slack App**
   - Create a new Slack app at [api.slack.com](https://api.slack.com/apps)
   - Add the following OAuth scopes:
     - `chat:write`
     - `chat:write.public`
     - `channels:read`
     - `groups:read`
     - `im:read`
     - `mpim:read`
   - Enable Events API and set the Request URL to your *server*
   - Install the app to your workspace

## Usage

1. **Start the bot**
   ```bash
   python bot.py
   ```

2. **Bot Commands**
   - Type `start` in any channel to receive a welcome message
   - React to the welcome message to complete the onboarding task
   - Use `/message-count` slash command to check your message count

3. **Scheduled Messages**
   - Modify the `SCHEDULED_MESSAGES` list in `bot.py` to customize scheduled messages
   - Messages are automatically scheduled when the bot starts

## Configuration

### Bad Words Filter
Edit the `BADWORDS` list in `bot.py` to customize filtered words:
```python
BADWORDS = ['bad', 'no', 'ugly']  # Add your own words here
```

### Scheduled Messages
Modify the `SCHEDULED_MESSAGES` list to set up automated messages:
```python
SCHEDULED_MESSAGES = [
  {
    'text': 'Your message here',
    'post_at': int((datetime.now() + timedelta(seconds=20)).timestamp()),
    'channel': 'YOUR_CHANNEL_ID'
  }
]
```

### Welcome Message Customization
The welcome message can be customized in the `WelcomeMessage` class:
- Change the welcome text in `START_TEXT`
- Modify the emoji in `icon_emoji`
- Update the bot username in `get_message()`

## API Endpoints

- `POST /slack/events` - Slack Events API endpoint
- `POST /message-count` - Message count query endpoint

## Project Structure

```
Slack-Bot/
├── bot.py              # Main bot application
├── requirements.txt    # Python dependencies
├── .env                # Environment variables (create this)
├── .gitignore          # Git ignore file
└── README.md           # This file
```

## Dependencies

- `slackclient` - Slack API client
- `flask` - Web framework for handling HTTP requests
- `python-dotenv` - Environment variable management
- `slackeventsapi` - Slack Events API adapter


## Support

- Check the [Slack API documentation](https://api.slack.com/)