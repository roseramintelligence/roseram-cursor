# Roseram Cursor

A browser code workspace for opening one source file and asking questions about its implementation.

> **Current scope:** This repository publishes Roseram's current app source. It is an early browser/API client, not a native local-repository IDE or a clone of another company's private application.

## Upstream integration

Configure the Roseram model in VSCodium with Cline. [Setup instructions and configuration](upstream/README.md).

## What is included

- `src/index.mjs`: self-contained Node.js local web app and Roseram API client.
- `web/demo.html`: interactive sample with fictional content.
- `web/hosted-workspace.html`: browser workspace source used by the signed-in Roseram site.
- `web/roseram.webmanifest`: install metadata for the hosted Roseram route.

## Run the API client

Requires Node.js 22 or later and an eligible Roseram developer API key.

```sh
# Set ROSERAM_API_KEY in your shell; do not commit it.
npm start
```

The server binds to loopback, prints a local URL, and sends model requests to Roseram's API. The key is read from the environment or entered in the app. Treat it like a password and revoke it from your Roseram account if it is exposed.

## Roseram account integration

The live hosted route is [roseram.com/downloads/cursor](https://roseram.com/downloads/cursor). It uses Roseram sign-in, server-side plan/credit checks, and usage metering. The hosted workspace talks to the parent Roseram page using a restricted message bridge; the Node.js client instead uses a developer API key. A standalone repository clone does not independently implement Roseram account login or billing.

## Terminal workflow

Use Node.js 22 or later and set `ROSERAM_API_KEY` in your shell.

```sh
npm run terminal -- --mode edit --file src/index.mjs --prompt "Propose a clearer error message"
```

For available modes, run `npm run terminal -- --help`. An interactive terminal keeps the recent conversation in memory. Use `/clear` to reset it and `/quit` to exit. Model requests may use Roseram credits.

Repeat `--file` for up to 12 explicitly selected UTF-8 files under the current directory, totaling up to 48 KB. Selected text is sent with each request. Review proposals before applying changes to your project.

The [VS Code extension source](editor/README.md) adds a local key store, selection review and proposed edits in the editor diff view.

## Current limitations

The current browser client supports one supplied text file at a time (up to 65 KB). It does not connect to local folders, extensions, or a terminal.

Signed native desktop installers are not currently included. The Node.js package is an API client, not a desktop installer.

## Development

```sh
npm run check
npm run help
```

Contributions should preserve the MIT license and must not commit API keys, account data, or private customer material. See [CONTRIBUTING.md](CONTRIBUTING.md) and [SECURITY.md](SECURITY.md).

## Independence and names

This is an independent Roseram project. It is not affiliated with or an official client of any third-party AI, editor, or coding-agent vendor. No third-party proprietary source code is included.
