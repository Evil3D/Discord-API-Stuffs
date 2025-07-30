# ⚙️ Discord API Stuffs

> ⚠️ **Educational Purposes Only**  
> This project is meant to document how the Discord client interacts with its API.  
> It is not intended for abuse, automation, alt generation, or anything against [Discord’s Terms of Service](https://discord.com/terms).  
> Do not self-bot. Do not use this data maliciously.  
> This is just for learning, exploration, and testing.

---

## 📘 What is this?

Whenever I'm bored (which... is a lot), I open DevTools and poke around the Discord API to see what happens.  
This repo documents some of what I’ve discovered — especially request bodies (JSON) that aren't easily found anywhere else.

> Most endpoints were tested using [Discord Canary](https://canary.discord.com), since I'm fancy like that.

---

## 🧠 Why I Made This

I couldn't find a simple and up-to-date resource with actual API request payloads — not even Discord’s [official docs](https://github.com/discord/discord-api-docs) include this kind of stuff clearly.  
So I made my own, in a way that’s easy enough for even a monkey to understand.

---

## 📦 Channels

### Channel Creation

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
  "flags": 4295063878,
  "rate_limit_per_user": <0-21600>
}
```

> 📢 FYI: If im not mistaken, the user limit is for voice chat channels, i have no idea what the rate limit per user is for.

Types:
- 0 = text channel  
- 2 = voice channel  
- 4 = category (cannot have a parent_id)  
- 5 = announcement channel  
- 6 = store channel (deprecated, requires SKU ID)  
- 13 = stage channel  
- 14 = unknown/unused but valid  
- 15 = forum channel  
- 16 = media channel  

**Endpoint:**  
`POST https://canary.discord.com/api/v9/guilds/<GUILD_ID>/channels`

---

### Channel Editing

```json
{
  "id": "<channel_id>",
  "type": <list above>,
  "last_message_id": "<optional>",
  "flags": 0,
  "guild_id": "<guild_id>",
  "name": "<name>",
  "parent_id": "<category_id>",
  "rate_limit_per_user": 0,
  "topic": "",
  "position": 0,
  "permission_overwrites": [],
  "nsfw": false,
  "icon_emoji": {
    "id": null,
    "name": "👋"
  },
  "theme_color": null
}
```

> ❌ Editing doesn’t always work — may require proper headers or permissions.

**Endpoint:**  
`PATCH https://canary.discord.com/api/v9/channels/<CHANNEL_ID>`

---

## 🌐 Server Creation

```json
{
  "name": "<your server name>",
  "icon": "data:image/png;base64,<image>", // or null
  "guild_template_code": "2TffvPucqHkN", // default template
  "channels": [],
  "system_channel_id": null
}
```

**Endpoint:**  
`POST https://canary.discord.com/api/v9/guilds`

**Bonus Endpoint:**  
`DELETE https://canary.discord.com/api/v9/guilds/<GUILD_ID>`

---

## 🧑 Account Actions

### Username Availability Check

```json
{
  "username": "<desired_username>"
}
```

**Endpoint:**  
`POST https://discord.com/api/v9/unique-username/username-attempt-unauthed`

---

### Account Creation

```json
{
  "fingerprint": "",
  "email": "<email>",
  "username": "<username>",
  "global_name": "<display_name>",
  "password": "<password>",
  "invite": null,
  "consent": true,
  "date_of_birth": "yyyy-mm-dd",
  "gift_code_sku_id": null,
  "promotional_email_opt_in": false
}
```

> 🔐 Fingerprint might come from captcha or session — not always needed in test scenarios.

**Endpoint:**  
`POST https://discord.com/api/v9/auth/register`

---

### Account Verification

```json
{
  "token": "<verification_token>"
}
```

**Endpoint:**  
`POST https://discord.com/api/v9/auth/verify`

---

### Login

```json
{
  "login": "<email>",
  "password": "<password>",
  "undelete": false,
  "login_source": null,
  "gift_code_sku_id": null
}
```

**Endpoint:**  
`POST https://canary.discord.com/api/v9/auth/login`

---

### Forgot Password

```json
{
  "login": "<email>"
}
```

**Endpoint:**  
`POST https://canary.discord.com/api/v9/auth/forgot`

---

## 🏠 HypeSquad Badge

```json
{
  "house_id": 1
}
```

- 1 = Bravery (purple)  
- 2 = Brilliance (red)  
- 3 = Balance (cyan)

**Endpoint:**  
`POST https://canary.discord.com/api/v9/hypesquad/online`

---

## 📹 Skip Video Quest

```json
{
  "timestamp": 999
}
```

**Endpoint:**  
`POST https://canary.discord.com/api/v9/quests/<quest_id>/video-progress`

---

## 💬 Group DM Creation

```json
{
  "recipients": []
}
```

> You can leave `recipients` empty to make a group DM with just yourself.

**Endpoint:**  
`POST https://canary.discord.com/api/v9/users/@me/channels`

## ✉️ Invite Creation

```json
{
  "max_age": 0,
  "max_uses": 0,
  "target_type": null,
  "temporary": true,
  "flags": 0
  "validate": "<invite code>" //run the first time, the second, flags are added
}
```

**Endpoint:**
`POST api/v9/channels/<channel_id>/invites

---

## 🧪 Notes

- Most of this is gathered from personal testing in browser DevTools.
- You **must** have the right headers/tokens to use these endpoints.
- Never share your Discord token.
- Do **not** use this information to violate TOS — this is strictly educational.

---

## 📜 Legal & TOS

This is a learning project only.  
It is not affiliated with or endorsed by Discord.  
You are responsible for how you use this data. Use it wisely and ethically.

---

## 💡 Contributions

Found a new payload or experimental feature?  
Feel free to submit a PR or open an issue to contribute.
