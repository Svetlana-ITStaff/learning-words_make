# learning-words_make

# Google Sheets → Telegram: 5 Random Words (Make.com Scenario)

A Make.com (Integromat) scenario that:
1) Reads rows from a Google Sheet (columns A–C),
2) Aggregates them into an array,
3) Picks 5 random rows,
4) Sends the result to a Telegram chat.

This is useful for language learning (e.g., sending a daily set of random words to a Telegram bot/chat).

---

## How It Works

### Modules
1. **Google Sheets — Filter/Search Rows**
   - Reads data from `Sheet1`
   - Range: `A1:CZ1`
   - Assumes the sheet has headers

2. **Basic Aggregator**
   - Collects sheet rows into a single array

3. **Set Variables (random01–random05)**
   - Generates five random indices based on array length

4. **Set Variables (word01–word05)**
   - Builds 5 strings in format:  
     `Croatian - Transliteration - Translation`

5. **Telegram — Send Message**
   - Sends a formatted message with 5 random words to your chat

---

## Google Sheet Format

Your sheet should have at least these columns:

| Column | Meaning |
|--------|---------|
| A | Croatian |
| B | Transliteration |
| C | Translation |

Example row:
- `dobar dan` | `dobar dan` | `hello`

---

## Setup

### 1) Import the Scenario to Make.com
- Create a new scenario in Make.com
- Import the `scenario.json` file from this repository

### 2) Configure Connections
Replace placeholders in `scenario.json` or update settings after import:
- `{{GOOGLE_CONNECTION_ID}}` → your Google connection in Make
- `{{TELEGRAM_CONNECTION_ID}}` → your Telegram bot connection in Make

### 3) Set Spreadsheet and Chat IDs
- `{{SPREADSHEET_ID}}` → Google Spreadsheet ID (from the URL)
- `{{TELEGRAM_CHAT_ID}}` → your Telegram chat ID

Tip:
- To find a chat ID, you can use a Telegram “getUpdates” method or a helper bot like @userinfobot.

---

## Customization

### Change number of words
- Add/remove random variables (`random06`, etc.)
- Add/remove word variables (`word06`, etc.)
- Update Telegram message template accordingly

### Avoid duplicates
Current logic can pick the same row more than once.
To avoid duplicates:
- Generate a shuffled list of indices and take the first 5
- Or store used indices in an array and re-roll when duplicate appears

### Change message language / format
Edit the Telegram text template in the last module:
```text
Here are 5 new words...

{{word01}}
...
