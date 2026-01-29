# Installing Clawdbot iOS (Without a Mac)

This guide helps you install the Clawdbot iOS app on your iPhone **without owning a Mac**.

## Option 1: GitHub Actions Auto-Build (Recommended)

### How it works:
1. GitHub Actions automatically builds the iOS app using macOS runners
2. Downloads the unsigned `.ipa` file
3. Sideload it using AltStore or Sideloadly

### Steps:

1. **Trigger the build:**
   - Go to: https://github.com/Atlas-Os1/atlas/actions
   - Click "iOS App Build" workflow
   - Click "Run workflow" → "Run workflow"
   - Wait 5-10 minutes for build to complete

2. **Download the IPA:**
   - Click on the completed workflow run
   - Scroll to "Artifacts" section
   - Download `Clawdbot-iOS-unsigned.zip`
   - Extract to get `Clawdbot-unsigned.ipa`

3. **Install on iPhone:**

   **Option A: AltStore (Free, recommended)**
   - Install AltStore on Windows/Linux: https://altstore.io
   - Connect iPhone via USB
   - Drag `Clawdbot-unsigned.ipa` into AltStore
   - Refresh every 7 days (free Apple ID limitation)

   **Option B: Sideloadly (Free)**
   - Download: https://sideloadly.io
   - Connect iPhone via USB
   - Select the IPA and sign with your Apple ID
   - Install to iPhone

   **Option C: TrollStore (Permanent, requires jailbreak/exploit)**
   - If your iPhone is compatible: https://github.com/opa334/TrollStore
   - Permanent install (no 7-day refresh needed)

## Option 2: Use iSH Shell (Current Setup)

Since you have iSH Shell installed, you can use it as a lightweight node:

### What you can do:
- SSH into your iPhone from Clawdbot gateway
- Run shell commands remotely
- Trigger iOS Shortcuts via URL schemes
- Access files on your iPhone

### Setup:
```bash
# In iSH Shell on iPhone
apk update
apk add openssh git nodejs npm

# Generate SSH key
ssh-keygen -t rsa -b 4096

# Set password
passwd

# Start SSH server
/usr/sbin/sshd -p 2222
```

### Connect from gateway:
```bash
# From your VPS
ssh -p 2222 root@100.101.101.125
```

## Option 3: Remote Mac Access (If you need to build locally)

### Cloud Mac services:
- **MacStadium**: ~$25/month (https://macstadium.com)
- **AWS EC2 Mac**: ~$1/hour (https://aws.amazon.com/ec2/instance-types/mac/)
- **MacinCloud**: ~$30/month (https://macincloud.com)

### Free alternatives:
- Borrow a friend's Mac for 30 minutes
- Use Apple Store demo Macs (save project to iCloud)
- Local library/university Mac labs

## Comparison

| Method | Cost | Setup Time | Renewal | Capabilities |
|--------|------|------------|---------|--------------|
| GitHub Actions + AltStore | Free | 15 min | Every 7 days | Full iOS app |
| iSH Shell | Free | 5 min | None | Shell access, limited |
| TrollStore | Free* | 30 min | None | Full iOS app (permanent) |
| Cloud Mac | $25-30/mo | 1 hour | Monthly | Full Xcode access |

*Requires compatible iOS version

## Next Steps

1. **Try iSH Shell first** (you already have it) - get SSH working
2. **Trigger GitHub Actions build** - get the full iOS app
3. **Install via AltStore** - easiest sideloading method

## Need Help?

- Discord: https://discord.com/invite/clawd
- GitHub Issues: https://github.com/Atlas-Os1/atlas/issues
