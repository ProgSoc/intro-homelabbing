---
theme: dracula
title: Intro to Home Labbing Part 1
layout: cover
drawings:
  enabled: false
info: |
  Workshop deck covering SSH access, Docker install, Docker Compose basics,
  and deploying Homarr on a VPS.
---

<style>
.slidev-layout h1,
.slidev-layout h2,
.slidev-layout h3 {
  line-height: 1.15;
  margin-bottom: 0.42em;
}

.slidev-layout h1 + p,
.slidev-layout h1 + ul,
.slidev-layout h1 + ol,
.slidev-layout h1 + pre,
.slidev-layout h2 + p,
.slidev-layout h2 + ul,
.slidev-layout h2 + ol,
.slidev-layout h2 + pre,
.slidev-layout h3 + p,
.slidev-layout h3 + ul,
.slidev-layout h3 + ol,
.slidev-layout h3 + pre {
  margin-top: 0.38em;
}

.slidev-layout p,
.slidev-layout li,
.slidev-layout td,
.slidev-layout th {
  font-size: 1.12em;
  line-height: 1.45;
}

.slidev-layout ul,
.slidev-layout ol {
  margin-top: 0.4em;
  margin-bottom: 0.65em;
}

.slidev-layout pre {
  font-size: 1.04em;
  margin-top: 0.72em;
  margin-bottom: 0.72em;
  padding: 0.65em 0.85em;
  border-radius: 10px;
}

.slidev-layout pre + pre {
  margin-top: 0.95em;
}

.slidev-layout code {
  font-size: 1.03em;
}
</style>

<script setup>
import csecLogo from './images/UTS.CSS-logo-white.png'
import progsocLogo from './images/progsoc-white.png'
</script>

# Intro to Home Labbing Part 1
## SSH, Docker, and Compose on a VPS

<div style="position:absolute;left:50%;bottom:26px;transform:translateX(-50%);display:flex;align-items:center;justify-content:center;gap:28px;">
  <img :src="csecLogo" alt="UTS Cyber Security Society" style="height:64px;width:auto;object-fit:contain;" />
  <div style="width:2px;height:56px;background:#6272a4;opacity:0.8;"></div>
  <img :src="progsocLogo" alt="ProgSoc" style="height:78px;width:auto;object-fit:contain;" />
</div>

<!--
- Welcome everyone and set expectations: beginner friendly, hands-on.
- Mention this is Part 1 and today we focus on fundamentals.
- 1 minute.
-->

---

<script setup>
import activateLogo from './images/ActivateUTS_Primary-Reverse_RGB.png'
import fortinetLogo from './images/FTNT_Lock_Up_Logo.png'
import bugcrowdLogo from './images/Wordmark-Orange-Bugcrowd.png'
import volkisLogo from './images/Volkis_Logo.png'
</script>

<div style="height:100%;box-sizing:border-box;display:flex;flex-direction:column;gap:10px;padding:2px 6px 0;">
<div style="text-align:center;">
<h1 style="margin:0;font-size:56px;line-height:1;color:#f8f8f2;font-weight:700;letter-spacing:0.02em;">Sponsors</h1>
<p style="margin:4px 0 0;font-size:16px;color:#bd93f9;">Thanks for supporting this workshop</p>
</div>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;">
<div style="background:linear-gradient(145deg,#3b3f52,#2f3242);border:2px solid #50fa7b;border-radius:18px;padding:10px 12px;min-height:168px;display:flex;flex-direction:column;">
<p style="margin:0;text-align:center;color:#f1fa8c;font-size:12px;letter-spacing:0.1em;text-transform:uppercase;">Primary</p>
<div style="flex:1;display:flex;align-items:center;justify-content:center;">
<img :src="activateLogo" alt="ActivateUTS" style="max-width:90%;max-height:78px;width:auto;" />
</div>
</div>
<div style="background:linear-gradient(145deg,#95ecff,#6ad6ee);border:2px solid #8be9fd;border-radius:18px;padding:10px 12px;min-height:168px;display:flex;flex-direction:column;">
<p style="margin:0;text-align:center;color:#1f2333;font-size:12px;letter-spacing:0.1em;text-transform:uppercase;">Platinum</p>
<div style="flex:1;display:flex;align-items:center;justify-content:center;">
<img :src="fortinetLogo" alt="Fortinet and NextGen" style="max-width:92%;max-height:72px;width:auto;" />
</div>
</div>
</div>
<div style="margin:0 auto;width:70%;background:linear-gradient(145deg,#f1fa8c,#e3f06a);border:2px solid #ffb86c;border-radius:18px;padding:10px 14px;min-height:165px;display:flex;flex-direction:column;">
<p style="margin:0;text-align:center;color:#2b3040;font-size:12px;letter-spacing:0.1em;text-transform:uppercase;">Gold</p>
<div style="flex:1;display:grid;grid-template-columns:1fr 1fr;align-items:center;justify-items:center;gap:14px;">
<img :src="bugcrowdLogo" alt="Bugcrowd" style="max-width:90%;max-height:62px;width:auto;" />
<img :src="volkisLogo" alt="Volkis" style="max-width:72%;max-height:112px;width:auto;" />
</div>
</div>
</div>

<!--
- Thank sponsors briefly.
- Keep this slide short: 20-30 seconds.
-->

---

<script setup>
import workshopQr from './images/github-pages-qr.png'
</script>

## Slides Link

Scan to open the live workshop slides:

`https://progsoc.github.io/intro-homelabbing/`

<div style="margin-top:12px;display:flex;justify-content:center;">
  <img :src="workshopQr" alt="QR code for intro-homelabbing pages" style="height:220px;width:220px;border-radius:12px;background:#fff;padding:10px;" />
</div>

<!--
- Ask everyone to scan now and keep the tab open.
- Mention this link is for slides/docs and updates after each push.
- 30-45 seconds.
-->

---
layout: section
---

# What We Will Build

<!--
- Transition slide for the workshop roadmap.
- 10 seconds.
-->

---

## Session Agenda (~40 min + break)

- Connect to the VPS and run first checks (5 min)
- Install Docker with the convenience script and verify (8 min)
- Learn Compose essentials and core commands (7 min)
- Deploy Homarr from `compose.yaml` and validate (13 min)
- Recap, Q&A, and next steps (7 min)

<!--
- Mention this is practical and students should run commands as you do.
- 1 minute.
-->

---

## Prerequisites

- Workshop handout with server IP, username, and password
- Local terminal (Linux/macOS/Windows)
- Stable internet connection

<!--
- Ask everyone to confirm they can see their handout details.
- If anyone is missing details, pause early.
- 1 minute.
-->

---

<script setup>
import repoQr from './images/github-repo-qr.png'
</script>

## Get the Workshop Files

You can run this right after you log in to your VPS.

Option A (recommended): clone with Git

```bash
git clone https://github.com/ProgSoc/intro-homelabbing.git
cd intro-homelabbing
```

Option B: in GitHub, click `Code` -> `Download ZIP`, then extract it.

Repo URL:

`https://github.com/ProgSoc/intro-homelabbing`

<div style="margin-top:8px;display:flex;justify-content:center;">
  <img :src="repoQr" alt="QR code for intro-homelabbing repository" style="height:180px;width:180px;border-radius:12px;background:#fff;padding:8px;" />
</div>

<!--
- Mention Git option is easiest for future updates (`git pull`).
- If `git` is missing on VPS: `sudo apt install -y git`.
- If someone used ZIP, that is completely fine for this workshop.
- 1 minute.
-->

---
layout: section
---

# 1) Connect to the VPS

<!--
- Start of first practical block.
- 10 seconds.
-->

---

## Login Method (Password)

For this workshop, everyone logs in with password auth:

```bash
ssh <user>@<vps-ip>
```

On first connection, type `yes` at the host key prompt, then enter password.

<!--
- Remind students password won't show while typing.
- Common issue: wrong username (`root` vs `ubuntu`).
- If login fails, verify username first, then password.
- 2 minutes.
-->

---

## First Checks After Login

```bash
# Show who you are logged in as
whoami
```

```bash
# Show host details (hostname, kernel, architecture)
hostnamectl
```

```bash
# Show Linux distro and version
lsb_release -a
```

<!--
- Confirm everyone is logged into the expected account.
- If `lsb_release` is missing, run `cat /etc/os-release` instead.
- 3 minutes.
-->

---
layout: section
---

# 2) Install Docker

<!--
- Transition to installation block.
-->

---

## Install Docker (Convenience Script)

```bash
sudo apt update && sudo apt upgrade -y
```

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
rm get-docker.sh
```

<!--
- Run update first, then install script.
- Mention convenience script is workshop-friendly and quick.
- Convenience script usually enables/starts Docker on Ubuntu.
- 4 minutes (allow slower VPSs).
-->

---

## Post-install Verification

Check Docker and Compose:

```bash
sudo docker version
sudo docker compose version
```

Run a test container:

```bash
sudo docker run --rm hello-world
```

Expected output includes: `Hello from Docker!`

<!--
- This is the confidence checkpoint before moving on.
- If Docker isn't running, use `sudo systemctl start docker` and retry.
- If image pull fails, usually DNS/internet issue on the VPS.
- 4 minutes.
-->

---
layout: section
---

# 3) Docker Compose Basics

<!--
- Transition to Compose concepts.
-->

---

## Compose File Essentials

- `services`: containers to run
- `ports`: host-to-container port mapping
- `volumes`: persist data on disk
- `environment`: configuration/secrets
- `restart`: restart policy after crashes/reboots

<!--
- Keep this conceptual and quick.
- Mention YAML indentation is critical.
- Compose is declarative: the file is your desired state.
- 2 minutes.
-->

---

## Compose Anatomy Example

```yaml
# Top-level section listing all containers
services:
  # Service name used by Compose
  web:
    # Image to run: <repo>:<tag>
    image: nginx:alpine
    # Port mapping: <host-port>:<container-port>
    ports:
      - "8080:80"
    # Restart automatically unless manually stopped
    restart: unless-stopped
    # Bind mount: <host-path>:<container-path>:<mode>
    volumes:
      - ./html:/usr/share/nginx/html:ro
```

<!--
- Walk line by line.
- Explain why `:ro` is useful for static content.
- 3 minutes.
-->

---

## Commands You Will Use Most

```bash
sudo docker compose up -d      # start in background
sudo docker compose ps         # list running services
sudo docker compose logs -f    # live logs
sudo docker compose pull       # download new images
sudo docker compose down       # stop and remove containers
```

<!--
- Teach up/ps/logs first; pull/down are maintenance commands.
- 2 minutes.
-->

---
layout: section
---

# 4) Deploy Homarr

<!--
- Transition to capstone deployment.
-->

---

## Open the Homarr Example

```bash
cd ~/intro-homelabbing/examples/homarr
ls
```

This folder already includes the workshop `compose.yaml`.

<!--
- If someone cloned elsewhere, adjust the path.
- 1 minute.
-->

---

## Homarr `compose.yaml`

Already included in the repo at `examples/homarr/compose.yaml`:

```yaml
services:
  homarr:
    image: ghcr.io/homarr-labs/homarr:latest
    container_name: homarr
    restart: unless-stopped
    ports:
      - "7575:7575"
    environment:
      - SECRET_ENCRYPTION_KEY=${SECRET_ENCRYPTION_KEY}
    volumes:
      - ./appdata:/appdata
      - /var/run/docker.sock:/var/run/docker.sock:ro
```

<!--
- Mention `/var/run/docker.sock` is powerful; keep it read-only.
- Remind students: compose file and .env must be in same directory.
- 4 minutes.
-->

---

## Create `.env` Secret

In `~/intro-homelabbing/examples/homarr`:

1) Generate a key:

```bash
openssl rand -hex 32
```

2) Create `.env`:

```bash
echo "SECRET_ENCRYPTION_KEY=<paste-generated-key>" > .env
cat .env
```

3) Deploy:

```bash
sudo docker compose up -d
```

<!--
- Paste the generated key exactly; no quotes needed.
- If .env has wrong key name, Homarr will fail to start.
- Common typo: `SECRET_ENCRYPTION_KEY` misspelled.
- 4 minutes.
-->

---

## Validate the Deployment

```bash
sudo docker compose ps
sudo docker compose logs -f homarr
```

Open in browser:

```text
http://<vps-ip>:7575
```

<!--
- Check container status is Up.
- In logs, look for startup complete/no fatal errors.
- If page does not load, re-check VPS IP and port `7575`.
- 3 minutes.
-->

---

## Updating Homarr Later

```bash
cd ~/intro-homelabbing/examples/homarr
sudo docker compose pull
sudo docker compose up -d
sudo docker image prune -f
```

For normal updates, you do **not** need `sudo docker compose down` first.

<!--
- Explain pull + up -d as standard update flow.
- `down` is only needed for teardown/troubleshooting.
- Keep prune optional but useful for small VPS disks.
- 1 minute.
-->

---
layout: section
---

# Pizza Time 🍕

Grab a slice and take a short break.

After pizza, try one of the extra stacks in `examples/`.

<!--
- Encourage students to test whoami/it-tools/uptime-kuma/linkding.
- 5 minutes (break; separate from the 40-minute core agenda).
-->

---

<script setup>
import csecLogo from './images/UTS.CSS-logo-white.png'
import progsocLogo from './images/progsoc-white.png'
</script>

## Recap

- You logged into a VPS with SSH
- Installed Docker and Compose on a Linux VPS
- Learned core Compose syntax and commands
- Deployed a real self-hosted app (Homarr)

<div style="position:absolute;left:50%;bottom:26px;transform:translateX(-50%);display:flex;align-items:center;justify-content:center;gap:26px;">
  <img :src="csecLogo" alt="UTS Cyber Security Society" style="height:48px;width:auto;object-fit:contain;" />
  <div style="width:2px;height:42px;background:#6272a4;opacity:0.8;"></div>
  <img :src="progsocLogo" alt="ProgSoc" style="height:56px;width:auto;object-fit:contain;" />
</div>

<!--
- Close with Q&A.
- Point to repo examples for post-workshop practice.
- 7 minutes.
-->
