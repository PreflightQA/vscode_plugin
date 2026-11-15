# Preflight for VS Code

Preview HTML email in supported email clients and light or dark modes from
GitHub Copilot. Preflight returns a browser gallery with live progress. VS Code
can also show an inline results panel when experimental MCP Apps are available.

## Install and connect

Use VS Code desktop with GitHub Copilot and read access to this repository.

1. Select the **Copilot** harness in VS Code Chat. Run
   **Chat: Install Plugin from Source** and enter
   `https://github.com/PreflightQA/vscode_plugin.git`. You can also clone the
   repository with your GitHub credentials and select that local folder.
2. Run **Chat: Open Customizations**. In **Plugins**, check that Preflight is
   enabled. In **MCP Servers**, open the Preflight server actions and select
   **Authenticate** if prompted. A Preflight organisation admin selects and
   authorises the organisation in the browser.
3. Ask “Which email clients and modes can I test, and how many credits do I
   have?” to verify the connection for free.

## Render and review

Use `/preflight` or ask Copilot to render supplied HTML or an HTML
email from a workspace file. Specify the client and mode for each screenshot.
Preflight charges one credit per accepted client and mode, including failed
captures. Client discovery, credit checks, and result reads are free.

Open **View screenshots** in the chat response to follow queued and running
captures and review them as they become available. Use the same gallery for
later status checks and comparisons.

## Smoke test

With a clean VS Code profile and a Preflight test organisation, verify
installation from both a local checkout and the private Git URL.

1. Check the client catalogue and remaining credits after browser sign-in.
   Both calls should succeed without a charge.
2. Render a synthetic HTML file in two supported clients in the same mode.
   Check that the gallery opens while captures are queued and that two credits
   are charged.
3. Check the same run's status. Verify the original gallery remains usable and
   the credit balance stays the same. If an inline panel appears, verify that
   it updates and that **Refresh** only reads results.
4. Repeat the status check with MCP Apps disabled and confirm the gallery
   remains accessible in ordinary chat text.
