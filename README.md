# Wordle By FULLYERIK

A desktop Wordle game built in C# with Windows Forms, backed by an online database for a shared leaderboard and custom word management.

## About

This is my take on the classic word-guessing game, rewritten from scratch as a native Windows application. Instead of keeping everything local, the game connects to a cloud database so scores and the word list are shared across anyone who plays. I built it to get more comfortable with C#, asynchronous networking, and designing a custom UI from the ground up.

The whole interface is custom-drawn — no default Windows window chrome. That includes the title bar, rounded buttons, an on-screen keyboard, and a full light/dark theme that can be switched on the fly.

## Features

- **Classic Wordle gameplay** — guess a five-letter word in six tries, with the familiar green / yellow / grey colour feedback
- **Online leaderboard** — every result is saved to a cloud database; players are ranked by points, with wins, losses, games played and average attempts tracked per name
- **Custom word management** — add or remove words from the shared list directly inside the app, with input validation
- **Light & dark mode** — toggle the theme from any screen, applied instantly everywhere
- **Custom app shell** — hand-built title bar with back, minimise, theme and close controls; the window is fully draggable
- **Dual input** — type with your physical keyboard or click the built-in on-screen keyboard; both stay colour-synced with your guesses
- **Scoring system** — fewer guesses means more points (6 points for a first-try win down to 1 point for a sixth-try win, 0 for a loss)

## Tech Stack

- **C# / .NET 8** with **Windows Forms** for the UI
- **Supabase** (PostgreSQL) as the backend, accessed through its REST API
- Pure `HttpClient` + `System.Text.Json` for networking — no heavy third-party dependencies

## How It Works

The game talks to the database over a small service layer that wraps the REST endpoints for reading the word list, picking a random secret word, and updating player statistics after each round. Player stats accumulate across sessions, so playing again under the same name adds to your totals rather than replacing them.

The colouring logic handles repeated letters correctly — a guessed letter only lights up as many times as it actually appears in the answer, which is the part of Wordle most clones get wrong.

## Roadmap

Some ideas I might add later:

- Flip animations when revealing letter colours
- Sound effects for typing and winning
- A daily-word mode where everyone gets the same puzzle
- A per-player statistics screen

## Author

Built by **FULLYERIK**.
