# Roseram with VSCodium and Cline

Install [VSCodium](https://vscodium.com/install/) and add [Cline](https://github.com/cline/cline) from an official extension release. In Cline's provider settings choose **OpenAI Compatible** and use the values in [cline-provider.json](cline-provider.json). Enter your Roseram developer key in the API key field.

The JSON file is a settings reference. Enter the values using the extension UI. Keep automatic approvals off for the first session and check the proposed changes in a test project. This configuration uses Roseram's Chat Completions endpoint.

This repo also includes the [Roseram editor extension](../editor/README.md) for selection review and diff previews.

Upstream source and licensing: [VSCodium](https://github.com/VSCodium/vscodium), [Code OSS](https://github.com/microsoft/vscode/blob/main/LICENSE.txt) and [Cline, Apache-2.0](https://github.com/cline/cline).
