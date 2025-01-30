# Git Auto Watch 🔄

Automatically monitor your Git repository and push changes whenever files are modified. Perfect for development environments where frequent commits are needed.

---

## Features ✨

- **Auto-Commit & Push**: Automatically stages, commits, and pushes changes
- **Detached Mode**: Run as background process
- **Custom Commit Messages**: Optional user-defined messages
- **SSH Key Support**: Specify SSH keys for authentication
- **Process Management**: Start/stop background tasks
- **Live Logging**: Monitor activity in real-time
- **Cross-Platform**: Works on Linux, macOS, and WSL

---

## Installation ⚙️

### Requirements
- `fswatch` (will be auto-installed if missing)
- Git
- SSH key configured with your Git provider

### 1. Install Script
```bash
sudo curl -L https://raw.githubusercontent.com/rajsubhod/git-auto-watch/main/git_auto_watch \
  -o /usr/local/bin/git_auto_watch
sudo chmod +x /usr/local/bin/git_auto_watch
```

## Verify Installation
```
git_auto_watch --help
```

## Usage 🚀
### Basic Monitoring
```
git_auto_watch /path/to/your/repo
```

### Detached Mode (Background)
```
git_auto_watch /path/to/your/repo --detach
```

### With Custom Commit Message
```
git_auto_watch /path/to/repo -m "Database schema updates"
```

### Using Specific SSH Key

```
git_auto_watch /path/to/repo -i ~/.ssh/github_key
```

### View Live Logs


```
git_auto_watch --logs
```

### Stop Background Process
```
git_auto_watch --stop
```

## Configuration ⚙️

| Option              | Description              | Default                   |
|---------------------|--------------------------|---------------------------|
| `--log-file <path>` | Custom log file path     | `/tmp/git_auto_watch.log` |
| `--branch <name>`   | Specify Git branch       | `main`                    |


## Troubleshooting 🔧
### SSH Passphrase Prompts

```
# Start SSH agent and add key
eval $(ssh-agent)
ssh-add ~/.ssh/your_key  # Enter passphrase once
```

### Process Not Stopping
```
# Manual cleanup if --stop fails
pkill -f "fswatch|git_auto_watch"
rm -f /tmp/git_auto_watch.pid
```

### False Change Detection
```
# Check ignored files in .gitignore
git check-ignore -v filename
```

### View Full Logs
```
tail -n 100 /tmp/git_auto_watch.log
```

## How It Works 🛠️

1. File Monitoring: Uses `fswatch` to detect file system changes

2. Change Validation: Checks `git status` for actual modifications

3. Commit & Push:

    - Stages all changes (`git add .`)

    - Creates timestamped commit

    - Pushes to remote repository

4. Detached Mode:

    - Runs as background process

    - Maintains SSH agent context

    - Logs all activity to file

## Limitations ⚠️

- ❌ Doesn't handle merge conflicts

- ❌ Not recommended for production environments

- ❌ Requires write permissions to remote repository

# Contributing 🤝

1. Fork the repository

2. Create feature branch (git checkout -b feature/awesome)

3. Commit changes (git commit -am 'Add awesome feature')

4. Push to branch (git push origin feature/awesome)

5. Open Pull Request

## License 📜

MIT License - See LICENSE for details
Copy

```
This README includes:
1. Clear installation instructions
2. Usage examples with common scenarios
3. Troubleshooting common issues
4. Technical implementation details
5. Contribution guidelines
6. License information

You can customize the URLs and add screenshots/demos as needed. Would you like me to create any specific section in more detail?
```