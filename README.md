# Solarchik — Anna AI App Builder Program

Voice AI friend, runner companion, and call secretary.

Same product as Solarchik. Separate repository for the [Anna AI App Builder Program](https://dorahacks.io/hackathon/2349).

This repo does **not** contain Solana Mobile CLOCK IN.

**Hackathon:** Anna AI App Builder Program  
**Platform:** [anna.partners/developers](https://anna.partners/developers)  
**DoraHacks:** [dorahacks.io/hackathon/2349](https://dorahacks.io/hackathon/2349)  
**Prize pool:** $6,000  
**Deadline:** 31 October 2026 (extended)  
**Team:** Solar DePin · Vadym Bilobrovets (`mcBanCh`)

## What judges should see

Solarchik is one everyday workflow: a person who cannot pick up every call still needs a secretary who knows the known numbers, takes a message, and writes a short summary the human can approve.

On Anna that becomes an installable app:

- App UI for the secretary desk (call / known-unknown / summary / human review)
- Host LLM + storage instead of a custom agent stack
- `SKILL.md` so chat can `#mention` Solarchik and run the same workflow inline
- Human review before anything leaves the desk

## This repo vs other Solarchik repos

| Repo | Track |
| --- | --- |
| [mcBanCh/solarchik-anna-2026](https://github.com/mcBanCh/solarchik-anna-2026) | Anna AI App Builder Program |
| [mcBanCh/solarchik-munichtech-2026](https://github.com/mcBanCh/solarchik-munichtech-2026) | MunichTech EXPO 2026 |
| [mcBanCh/Solarchik](https://github.com/mcBanCh/Solarchik) | Solana Mobile CLOCK IN — do not mix |

## Build later

```bash
anna-app init solarchik
anna-app dev
anna-app publish
```

Docs: https://anna.partners/developers  
Examples: https://github.com/whtcjdtc2007/anna-executa-examples  
Platform docs: https://github.com/Anna-Partners/anna-developer-docs

## Status

Scaffold only. App UI, Host API wiring, and publish come next.
