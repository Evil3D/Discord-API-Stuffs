# Discord API Stuffs

Basically when im bored (which... is alot) i sometimes js do random shi- stuff and look at my network console thing and see what happens so this is basically that (nice..).

Also this isnt really anything advanced (imo atleast), short tutorial: open up google console (or dev tools idk the official name, call it wtv) using Ctrl + Shift + I (incase you didnt know) and go to the network tab (if it doesnt show up press the double arrow to add it) and just do something, like making a channel.

FYI: dont mind the text being red, it's just markdown being mad frfr..

### Channels
```json
{
  "name": "<your channel name>",
  "parent_id": "<category ID if any>",
  "permission_overwrites": [],
  "type": <list below> // Ignore the red, markdown's just mad.
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

### Creating Server
```json
{
  "name": "<your server name>"
  "icon": "data:image/png;base64, <image in b64 format>"
  "guild_template_code": "2TffvPucqHkN" // default, if none selected
  "channels": []
  "system_channel_id": "<so the channel id for the joins/nitro boost thingy>" // not modifiable
}
```

API Endpoint: https://canary.discord.com/api/v9/guilds

bonus: https://canary.discord.com/api/v9/guilds/<GUILD_ID>/delete
