# Google Sheets Database

## Purpose

Google Sheets is used as a lightweight database for storing previously published quotes and preventing duplicate content.

## Spreadsheet

The workflow uses a Google Sheets spreadsheet as the quote database.

> The actual Spreadsheet ID and Google credentials are intentionally not included in this public repository.

Use the following placeholders when configuring the workflow:

- Spreadsheet ID: `YOUR_GOOGLE_SHEETS_SPREADSHEET_ID`
- Google Sheets Credential: `YOUR_GOOGLE_SHEETS_CREDENTIAL_ID`

## Main Usage

The workflow follows this process:

1. DeepSeek generates a new quote.
2. Previously stored quotes are retrieved from Google Sheets.
3. The `Check Similarity` Code node compares the new quote with existing quotes.
4. If the quote is duplicate or highly similar, the workflow sends the process back to DeepSeek to generate another quote.
5. If the quote is sufficiently different, the workflow continues.
6. The accepted quote is stored in Google Sheets after the duplicate check.
7. The quote is then sent to Telegram.

## Duplicate Detection

The workflow currently uses a similarity threshold of:

`0.75`

A quote that reaches or exceeds the configured similarity threshold is treated as a duplicate/similar quote and is regenerated.

## Security

No API keys, passwords, OAuth tokens, or private Google credentials should be stored in this repository.

All private credentials must be configured directly inside n8n.
