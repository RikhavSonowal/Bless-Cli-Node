# 🌐 Bless Network – Native Node Setup Guide (Docker)

Welcome to the **Bless Network** – a decentralized, people-powered compute infrastructure.

This guide helps you set up and manage a **Native Bless Node** using Docker. Whether you're new to nodes or experienced with decentralized systems, this guide ensures you can get started smoothly and reliably.

---

## 🛠️ Prerequisites

Before you begin, ensure you have the following:

* 💻 A computer with internet access (Windows, macOS, or Linux)
* 🐟 Docker installed: [Download Docker here](https://docs.docker.com/get-docker/)
* 📂 Basic terminal/command line knowledge

---

## ⚡ Quick Start: Run Your Bless Node in Minutes

### 🔹 Step 1: Create the Environment

1. Open your terminal and create a folder for your node:

```bash
mkdir bless-node && cd bless-node
```

2. Inside this folder, create a file named `.env` and add the following:

```env
NODE_ROLE=worker
BOOT_NODES=/ip4/143.244.211.194/tcp/9010/p2p/12D3KooWGuBya7RYHTzZmR7uLJYUXffSPuBUPKnmYSfsgwyjqFuw

# Optional: S3 Backup Configuration (Cloud)
AWS_ACCESS_KEY_ID=<s3_id>
AWS_SECRET_ACCESS_KEY=<s3_key>
KEY_PATH=<backup_key_path>
KEY_PASSWORD=<key_password>
```

> 🛡️ Replace the `<...>` placeholders with your actual credentials if you want to enable cloud backup with S3.

---

### 🔹 Step 2: Run the Node

In the same directory where your `.env` file is saved, run:

```bash
docker run -d \
  --name blessnetwork-node \
  -p 9527:9527 \
  --env-file .env \
  ghcr.io/blessnetwork/b7s:0.6.6.patch3
```

✅ Your Bless node is now live and contributing to the decentralized network!

---

## 🛠 Node Management

### 🔍 View Node Logs

To see real-time output from your node:

```bash
docker logs -f blessnetwork-node
```

---

### ⛔ Stop the Node

To gracefully stop your node:

```bash
docker stop blessnetwork-node
```

---

### 🗑 Remove the Node

If you want to remove the container:

```bash
docker rm blessnetwork-node
```

---

## 🔐 Identity Persistence (Don't Lose Your Node ID!)

Your node generates a unique identity. If you delete the container without backing it up, you'll lose that identity. There are two ways to preserve it:

---

### Option 1: Store Identity Locally (Recommended)

Run this command to store node identity in a local folder:

```bash
docker run -d \
  --name blessnetwork-node \
  -p 9527:9527 \
  --env-file .env \
  -v ${PWD}/node-data:/app/keys \
  ghcr.io/blessnetwork/b7s:0.6.6.patch3
```

📁 This saves your keys in `node-data/`, allowing you to restart without losing identity.

---

### Option 2: Cloud Backup with S3

If you're using AWS S3, ensure your `.env` has these fields filled:

```env
AWS_ACCESS_KEY_ID=your_aws_key
AWS_SECRET_ACCESS_KEY=your_aws_secret
KEY_PATH=s3/folder/for/identity
KEY_PASSWORD=your_password
```

Bless will automatically back up and restore your node identity from S3 on each launch.

---

## 📈 What's Next?

Your node is running. What now?

* Monitor it regularly with `docker logs -f blessnetwork-node`
* Use volume or S3 backup to protect identity
* Stay active in the Bless Network for rewards, growth, and contribution

---

## 📞 Need Help?

Join the community and support team:

* 🧠 [Discord Server](https://discord.gg/blessnetwork)
* 📜 [Official Documentation](https://thebless.network)
* 💬 Ask questions, share logs, and get setup help

---

## 💡 About Bless

Bless Network isn’t just infrastructure — it’s a movement.

By running a node, you’re joining a new internet era where compute power is community-powered. Welcome aboard.

---

**Bless On! 🩱🩱 | #PoweredByPeople | #TimeToBuild**

## Help & Support

**Follow official Docs for more info and Errors!**

**Join TG for more Updates**:  
[https://telegram.me/CryptoRikhav](https://telegram.me/CryptoRikhav)

If you have any issue, then open an issue on this repo or DM me on TG.

**Smooth Run Gensyn – Best of Luck!**
