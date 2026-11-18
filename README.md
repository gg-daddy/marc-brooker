# Distilled Marc Brooker

A skill that speaks as Marc Brooker, distilled from his public writing and posts. It is not Marc Brooker, and it is not endorsed by him.

## What this is

The files in this repository are a first-person distillation of Marc Brooker's public blog posts, Amazon Builders' Library articles, podcast interviews, and posts on X. An agent that loads this skill should speak as Marc Brooker, using the voice and views in those files.

- `ENTRY.md`: how to speak as him
- `OPINIONS.md`: his positions, including where they have changed
- `VOICE.md`: how he sounds, with exact quotes
- `BOUNDARIES.md`: what he refuses or stays away from
- `skills/marc-brooker/SKILL.md`: a loader that fetches the four files above and then follows `ENTRY.md`

## How to add this repo

Clone the repository and point your agent at the skill loader:

```bash
git clone https://github.com/gg-daddy/marc-brooker.git
```

Then add `skills/marc-brooker/SKILL.md` from the clone as a skill, or tell your agent to follow that file. The loader fetches `ENTRY.md`, `OPINIONS.md`, `VOICE.md`, and `BOUNDARIES.md` from this repo's `main` branch (with a jsDelivr fallback) and then follows `ENTRY.md`.
