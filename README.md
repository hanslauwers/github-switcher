# GitHub Switcher Project

## Project Overview
Building a multi-account GitHub configuration and switching tool called **GitHubSwitcher** (`ghsw`).

## Current Status
- ✅ Architecture and features designed
- ⏳ Ready to start implementation

## Tool Purpose
Simplify managing multiple GitHub accounts (personal, work, client projects, etc.).

## Planned Features

### 1. Account Management
- List all configured GitHub accounts
- Add new accounts with SSH key generation
- Remove accounts safely
- Show current active account

### 2. Smart Switching
- Auto-detect account based on remote URL
- Manual switching with simple commands
- Context-aware suggestions

### 3. SSH Key Management
- Generate SSH keys for new accounts
- Test SSH connections
- Show key fingerprints and status

### 4. Git Configuration
- Set user.name and user.email per repository
- Manage global vs local configurations
- Backup/restore Git configs

## Planned CLI Commands
```bash
ghsw list                    # Show all accounts
ghsw add <name> <email>      # Add new account
ghsw switch <account>        # Switch to account
ghsw current                 # Show current account
ghsw auto                    # Auto-detect and switch
ghsw test [account]          # Test SSH connection
ghsw clone <url> [account]   # Clone with specific account
```

## `ghsw auto` Detection Logic
1. **Remote URL Analysis** - Parse SSH config hostnames
2. **Repository Pattern Matching** - Check path patterns (/work/, /personal/, /projects/)
3. **Existing Git Config** - Read current user.email
4. **Directory Context** - Check parent directory hints

### Example Auto-Detection:
```bash
$ ghsw auto
✓ Detected remote: github.com-personal:username/my-tool.git
✓ Switching to account: personal (user@example.com)
✓ Updated Git config for this repository
✓ SSH key ready: ~/.ssh/id_ed25519_personal
```

## Technical Implementation Plan
- **Language**: Python (good for file manipulation, CLI, subprocess calls)
- **Structure**:
  - Config file to store account info
  - SSH config management
  - Git config management
  - Simple CLI with argparse

## Example Environment Setup
- Git repository initialized
- SSH configured for multiple accounts:
  - `github.com-work` (work account)
  - `github.com-personal` (personal account)
- SSH keys:
  - `~/.ssh/id_ed25519_personal` (for personal@example.com)
  - `~/.ssh/id_ed25519_work` (for work@company.com)

## Next Steps When Resuming
1. Create project structure and initial Python files
2. Implement SSH key management functionality
3. Build account detection and switching logic
4. Add Git configuration management
5. Create CLI interface and commands
6. Test with existing accounts (work + personal)

## Getting Started
1. Clone this repository
2. Follow the setup instructions to configure your accounts
3. Start using `ghsw` commands to manage your GitHub workflows

---
*A CLI tool to simplify multi-account GitHub workflows*