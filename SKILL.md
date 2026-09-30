# Solarchik Secretary

A call-screening companion. The human keeps the address book on the phone. Solarchik only receives the caller number plus known/unknown, takes a message, and drafts a short summary for human review.

## When to trigger

- User mentions a missed call, unknown caller, or wants a secretary.
- User says `#solarchik` in Anna chat.
- User asks to summarize a voicemail or decide whether to call back.

## What the skill does

1. Read caller number and known/unknown flag. Do not request the full address book.
2. Draft a greeting and a one-paragraph summary of the message.
3. Stop for human review before sending any reply or callback note.
4. Save the approved summary in app storage.

## What the skill does not do

- Does not read contacts itself.
- Does not place a live phone call from Anna without explicit human approval.
- Does not mix in Solana Mobile CLOCK IN, wallets, or on-chain signatures.
