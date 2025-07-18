# Discord-API-Stuffs

Basically when im bored (which... is alot) i sometimes js do random shi- stuff and look at my network console thing and see what happens so this is basically that (nice..).
Also this isnt really anything advanced (imo atleast), short tutorial: open up google console (or dev tools idk the official name call it wtv) using Ctrl + Shift + I (incase you didnt know) and go to the network tab (if it doesnt show up press the double arrow to add it) and just do something, like making a channel.

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
5 = announcement channel,
13 = stage channel,
15 = forum channel,
16 = media channel

API Endpoint: https://canary.discord.com/api/v9/guilds/<GUILD_ID>/channels

