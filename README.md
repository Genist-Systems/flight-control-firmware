# 🚀 Flight Control Firmware Setup Guide

This repository contains the PX4-based flight control firmware. The link to this repository is shown above, and as of now, it should be **publicly accessible**.

---

## 📥 Cloning the Repository

To get started, you **must clone the repository using Git** with submodules included. Run the following command in your terminal:

```bash
git clone https://github.com/Genist-Systems/flight-control-firmware --recursive
```

⏱️ **Note:** This may take **10–20 minutes** depending on your internet connection speed.

Once cloning is complete, verify that all submodules are properly initialized and synced by running:

```bash
git submodule update --init --recursive
git submodule sync
```

---

## 🐳 Building the Firmware Using Docker

This project uses Docker to provide a consistent build environment.

### 1. Install Docker

If Docker is not already installed, download and install it from:  
👉 [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

---

### 2. Navigate to the Repository

Once Docker is installed and running, open a terminal and move into the firmware directory:

```bash
cd flight-control-firmware
```

---

### 3. Clean and Compile

Run the following commands to clean previous builds and compile the firmware:

```bash
./Tools/docker_run.sh "make clean"
./Tools/docker_run.sh "make px4_fmu-v6x_default"
```

🛠️ This will build the firmware for the **Pixhawk V6X** flight controller.

⚠️ **Warnings** may appear during compilation — these are usually safe to ignore. Look out for actual **errors** that stop the build process.

---

## ✅ Final Notes

After successful compilation, the firmware binary should be ready for flashing or simulation.

If you encounter any issues, double-check:
- That Docker is running correctly.
- That all submodules are synced.
- That you are using the correct target: `px4_fmu-v6x_default`.

---

For further help, refer to the official PX4 documentation:  
📚 [https://docs.px4.io](https://docs.px4.io)


---

## 🔑 Switching to SSH (Optional)

If you'd prefer to use SSH instead of HTTPS for Git operations, you can switch your remote URL with the following command:

```bash
git remote set-url origin git@github.com:Genist-Systems/flight-control-firmware.git
```

To verify the change:

```bash
git remote -v
```

You should see:

```
origin  git@github.com:Genist-Systems/flight-control-firmware.git (fetch)
origin  git@github.com:Genist-Systems/flight-control-firmware.git (push)
```

Make sure your SSH key is added to your GitHub account. Refer to [GitHub SSH key setup](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) if needed.


---

## 🔐 Setting Up SSH for GitHub

To use SSH with GitHub, follow these steps:

### 1. Check for an Existing SSH Key

Run the following command in your terminal:

```bash
ls -al ~/.ssh
```

Look for files named `id_rsa` and `id_rsa.pub` or similar. If they exist, you already have an SSH key.

---

### 2. Generate a New SSH Key (If Needed)

If you don’t have one, generate a new key:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Press `Enter` to accept the default file location. Set a passphrase if you want (optional but recommended).

---

### 3. Add SSH Key to ssh-agent

Start the ssh-agent and add your key:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

### 4. Add SSH Key to GitHub

Copy your public key to the clipboard:

```bash
cat ~/.ssh/id_ed25519.pub
```

Then go to **GitHub > Settings > SSH and GPG keys > New SSH key**, paste your key, and save.

Docs: [GitHub SSH key setup](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

---

### 5. Test Your SSH Connection

Verify it’s working:

```bash
ssh -T git@github.com
```

You should see a message like:  
`Hi your-username! You've successfully authenticated...`

---

You can now safely clone or push via SSH:
```bash
git clone git@github.com:Genist-Systems/flight-control-firmware.git --recursive
```
