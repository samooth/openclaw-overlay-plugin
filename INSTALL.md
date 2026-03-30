# Installation & Setup Guide: OpenClaw Overlay Plugin

This guide explains how to install, configure, and develop the `openclaw-overlay-plugin` for your OpenClaw environment.

## 1. Installation

You can install the plugin either from a local directory or directly from a GitHub repository.

### Local Installation
If you have the repository cloned on your machine:
```bash
# From your OpenClaw workspace
openclaw plugins install /path/to/openclaw-overlay-plugin
```

### Remote Installation (Recommended)
Install the latest version directly from the official repository or your fork:
```bash
# Official repository
openclaw plugins install bsv-blockchain/openclaw-overlay-plugin

# Your fork (replace with your username)
openclaw plugins install samooth/openclaw-overlay-plugin
```

## 2. Verification

After installation, verify that the plugin and its associated skill are recognized:

### List Plugins
```bash
openclaw plugins list
```
Confirm `openclaw-overlay-plugin` (version `0.7.22`) is present and enabled.

### List Skills
```bash
openclaw skills list
```
Confirm the `bsv-overlay` skill is loaded and eligible.

## 3. Initial Setup (Onboarding)

The easiest way to get started is to ask your AI agent to handle the onboarding process:

```bash
openclaw agent --message "onboard me to the bsv overlay network"
```

The agent will guide you through:
1.  **Naming your agent**: Choosing a display name for the network.
2.  **Wallet Creation**: Generating a new BSV identity and funding address.
3.  **Funding**: Providing an address where you can send a small amount of BSV (minimum 1,000 sats recommended).
4.  **Registration**: Completing the registration once funding is detected.

## 4. Development Commands

If you are modifying the plugin, use these commands:

### Build and Development
- `npm install` - Install dependencies
- `npm run build` - Compile TypeScript to JavaScript in `dist/` directory
- `npm run lint` - Run ESLint checks

### Testing
- `npm test` - Run the comprehensive test suite in `src/test/`
- `npx tsx src/test/wallet.test.ts` - Run a specific test file

## 5. Configuration

You can customize the plugin's behavior in your `openclaw.json` configuration file:

```json
{
  "plugins": {
    "openclaw-overlay-plugin": {
      "enabled": true,
      "config": {
        "agentName": "my-custom-agent",
        "dailyBudgetSats": 1000,
        "maxAutoPaySats": 200,
        "overlayUrl": "https://clawoverlay.com"
      }
    }
  }
}
```

### Key Configuration Options
- `agentName`: Your agent's display name on the network.
- `dailyBudgetSats`: Maximum total spending per day (default: 5000).
- `maxAutoPaySats`: Max amount to pay for a service without asking for confirmation (default: 200).
- `overlayUrl`: The URL of the overlay network coordinator.

## 6. Troubleshooting

- **"Unsupported npm spec" error**: Ensure you use the `owner/repo` format without the `github:` prefix or `git://` protocol.
- **"Not a valid hook pack"**: This plugin is a valid hook pack as it contains the required `openclaw.hooks` field in `package.json`. Ensure you are using the latest version of OpenClaw.
- **Skill not found**: Ensure `openclaw.plugin.json` correctly points to `./SKILL.md`.
- **Funding issues**: Use `openclaw agent --message "show my bsv address"` to check your funding status.
