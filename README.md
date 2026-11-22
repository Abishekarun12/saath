# Saath

**The AI that listens when you feel alone, and then helps you reconnect with the people who matter.**

Saath is a wellbeing companion for people who overthink and feel lonely, built for India and the UAE (especially South Asian expats far from family).

## Features

- **Talk it out**: AI companion in English, Hinglish, Hindi, Malayalam, Tamil, Arabic and Urdu, with voice typing, read-aloud and memory of past chats. It suggests reaching out when you mention someone you miss.
- **Reality check**: separates what was actually said from what you're assuming, and offers kinder explanations and a draft message.
- **Reach out**: drafts three low-pressure messages and opens WhatsApp. It never sends anything by itself, and it follows up later ("Did they reply?").
- **Your people**: family and friends with their local time, a "good time to call" hint, an "All OK at home?" check, and gentle reminders.
- **Night mode**: brain dump kept till morning, 4-7-8 breathing, AI sleep stories, body scan.
- **Unsaid box**: private notes, plus rehearsing a hard conversation with the AI playing the other person.
- **People like me**: anonymous, AI-moderated peer circles.
- **Your patterns**: when your mind feels heaviest, by day and time.
- **Safety**: "Need help now" on every screen with UAE and India helplines, and crisis detection in chats.

## How it runs (zero cost)

`index.html` is a single self-contained page published as a Claude artifact. It uses the artifact runtime's capabilities:

| Capability | Used for |
|---|---|
| `sample` | AI replies (companion, reality check, drafts, stories, moderation) |
| `db` + `user` | Private per-person data under `data/users/<id>/`, and shared anonymous posts under `circle_posts/<id>` |
| `dictation` | Voice typing (Chromium browsers) |
| `tts` | Reading replies and stories aloud |

Declared capabilities:

```json
{
  "sample": {}, "user": {}, "dictation": {}, "tts": {},
  "db": { "rules": [
    { "path": "circle_posts", "read": "view", "write": "owner" },
    { "path": "circle_posts/{self}", "write": "interact" },
    { "path": "data/users/{self}", "write": "interact" }
  ] }
}
```

When opened outside Claude (e.g. as a plain file), the app still works and saves to the browser's localStorage, but AI, voice and circles are turned off.

## Testing

Share the artifact from claude.ai and give testers **Contributor** access so their data saves and they can post in circles.

## Disclaimer

Saath is a wellbeing companion, not therapy or medical care. In an emergency, call local emergency services.
