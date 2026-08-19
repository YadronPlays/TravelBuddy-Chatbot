# TravelBuddy — Travel Assistant Chatbot

A Python chatbot that helps users with travel planning through natural conversation — recognising intents via regex, remembering user details, and pulling structured travel information for countries and continents.

** Data Programming for AI coursework **

---

## Overview

TravelBuddy is a data-driven chatbot built for a Data Programming for AI coursework assignment. Rather than hard-coding responses, all intents, patterns, and replies are stored in a JSON dataset and loaded at runtime, so the bot's "knowledge" is fully separated from its logic.

The project focuses on practical NLP techniques achievable without a machine learning model: regex-based pattern recognition (including named capture groups and multi-variable extraction), dictionary-driven response generation, and a simple memory system that lets the bot recall information — like the user's name — later in the same conversation.

## Features

- **Intent recognition via regex** — patterns range from simple constant matches up to named groups and multi-variable segment matching (e.g. extracting a destination country directly from free-text input)
- **Data-driven responses** — all patterns and responses loaded from `intents.json`, not hard-coded in the notebook
- **Memory system** — captures user details (e.g. name) during conversation and reuses them in later responses
- **Automated travel info lookup** — recognises countries/continents in the dataset and returns relevant details (cities, things to do, visa rules, budget, flights); falls back to a generic helpful response for anything not in the dataset
- **Fallback handling** — keeps the conversation flowing gracefully when no pattern matches
- **Main loop with clean exit** — runs until the user types `exit` or `quit`

## Example Interaction

```
You: hi there
Bot: Hey! I'm TravelBuddy, your travel assistant. What's your name?
You: I'm Bimarsha
Bot: Nice to meet you, Bimarsha! Where are you thinking of travelling?
You: I want to go to Japan
Bot: Japan is a great choice, Bimarsha! Here's what I know: [cities, budget tips, visa info...]
You: exit
Bot: Safe travels, Bimarsha!
```

## Pattern Matching Examples

```python
# Named group — extracts how the user is feeling
"i am (?P<feeling>doing great|amazing|good|fantastic)"

# Named group — extracts destination country from free text
"i want to go to (?P<country>[A-Za-z ]+)"
```

Each intent supports multiple pattern variations so the bot can recognise different phrasings of the same underlying request.

## Tech Stack

- **Python** — core logic, regex (`re` module), JSON handling
- **Jupyter Notebook** — development and demo environment

## Project Structure

```
TravelBuddy/
├── travelbuddy.ipynb   # Main notebook — chatbot demo
├── intents.json        # Patterns, responses, and travel data
├── report.pdf          # Written report: script, pattern examples, techniques used
```

## Running It

```bash
git clone <repo-url>
cd TravelBuddy
jupyter notebook travelbuddy.ipynb
```
Run all cells and interact with the bot directly in the notebook.

## What I'd Improve Next

- Replace regex-only matching with a lightweight intent classifier for more flexible phrasing
- Expand the travel dataset beyond the current country/continent coverage
- Add persistent memory across sessions (currently resets each run)

---

*Built for the Data Programming for AI module at Goldsmiths, University of London.*
