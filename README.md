# Discord API Stuffs

Basically when im bored (which... is alot) i sometimes js do random shi- stuff and look at my network console thing and see what happens so this is basically that (nice..).

Also this isnt really anything advanced (imo atleast), short tutorial: open up google console (or dev tools idk the official name, call it wtv) using Ctrl + Shift + I (incase you didnt know) and go to the network tab (if it doesnt show up press the double arrow to add it) and just do something, like making a channel.

FYI: dont mind the text being red, it's just markdown being mad frfr..

FYI 2: all endpoints will be from canary, since im that cool yea.. yea...

### Channels
#### Creation
```json
{
  "name": "<name>",
  "parent_id": "<category_id>",
  "type": <types below>,
  "topic": "",
  "icon_emoji": {
    "id": null,
    "name": "👋"
  },
  "bitrate": 64000,
  "user_limit": <1-99>,
  "nsfw": false,
  "flags": 4295063878, //these are all of the flags possible for a channel (almost all)
  "rate_limit_per_user": <0-21600, in seconds>
}
```

0 = text channel,
2 = voice channel,
4 = category (cannot have a parent_id),
5 = announcement channel,
6 = Discord Store Channel, you need a SKU ID and since i do not have 1 or can't create 1 either i can't test it, 
13 = stage channel,
15 = forum channel,
14 = Unknown, but considered valid by discord,
16 = media channel

API Endpoint: https://canary.discord.com/api/v9/guilds/<GUILD_ID>/channels

#### Editing
```json
{
  "id": "<channel_id>",
  "type": <list above>,
  "last_message_id": "<im guessing this is optional>",
  "flags": 0,
  "guild_id": "<well guild id>",
  "name": "<name>",
  "parent_id": "<category_id>",
  "rate_limit_per_user": 0,
  "topic": "",
  "position": 0,
  "permission_overwrites": [],
  "nsfw": false,
  "icon_emoji": {
    "id": null,
    "name": "👋(this is the default)"
  },
  "theme_color": null // idek what this is
}
```
#### THE EDITING DOES NOT WORK AS FAR AS I KNOW. (i use bot tokens to test, not self-botting, also dont self-bot, it's against the TOS and mostly unethical)

API Endpoint: https://canary.discord.com/api/v9/channels/<CHANNEL_ID>

### Creating Server
```json
{
  "name": "<your server name>",
  "icon": "data:image/png;base64, <image in b64 format>", set to null if none.
  "guild_template_code": "2TffvPucqHkN", // default, if none selected
  "channels": [],
  "system_channel_id": "<so the channel id for the joins/nitro boost thingy>" // not modifiable, set to null, otherwise might error.
}
```

API Endpoint: https://canary.discord.com/api/v9/guilds

bonus: https://canary.discord.com/api/v9/guilds/<GUILD_ID>/delete
