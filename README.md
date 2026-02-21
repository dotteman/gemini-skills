# Gemini CLI & Skills Setup Guide 🚀

This repository contains my personal AI "brain" for the Google Gemini CLI. It transforms the standard chat tool into a specialized assistant for **DevOps Engineering** (Azure, Terraform, vSphere) and **Culinary Arts** (Recipes, Meal Planning).

Follow this guide to set up your environment from scratch on a new Mac.

---

## 📦 Part 1: Installation & Prerequisites

If you have never used the terminal on this computer, follow these steps in order to get the necessary software.

### 1. Open the Terminal
1. Press `Command ⌘` + `Space` to open Spotlight Search.
2. Type **Terminal** and press `Enter`.
3. You will see a window with a text prompt. This is where you run the commands below.

### 2. Check or Install Homebrew
*Homebrew is the "App Store" for the terminal. We need it to install software.*

**Check if you have it:**
Type `brew --version` and press Enter.
* **If you see a version number:** Skip to Step 3.
* **If you see "command not found":** Copy and paste this command:
  ```zsh
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```
  *(Follow the on-screen instructions. You may need to enter your Mac login password).*

### 3. Check or Install Node.js & npm
*Gemini is built on Node.js. We need to install it.*

**Check if you have it:**
Type `node -v` and press Enter.
* **If you see a version number (e.g., v20.x.x):** Skip to Step 4.
* **If you see "command not found":** Run this command:
  ```zsh
  brew install node
  ```

### 4. Install the Gemini CLI
*This installs the official Google AI tool.*

Run this command:
```zsh
npm install -g @google/gemini-cli
```
**Verify installation:**
```zsh
gemini --version
```

---

## ⚙️ Part 2: Configure Your Environment

Now that the software is installed, we need to download your skills and configure the system to use the smartest AI model.

### 1. Download Your Skills
We need to clone this repository into the specific folder where Gemini looks for skills (`~/.gemini/skills`).

Run these commands exactly:

```zsh
# 1. Create the directory (if it doesn't exist)
mkdir -p ~/.gemini/skills

# 2. Clone this repo into that folder
# (Replace YOUR_USERNAME below with your actual GitHub username)
git clone https://github.com/dotteman/gemini-skills.git ~/.gemini/skills
```

### 2. Configure Shell Settings (Crucial Step)
We need to edit your terminal's configuration file (`.zshrc`) to force Gemini to use the **3.1 Pro Preview** model and add shortcuts for syncing your work.

1.  **Open your configuration file:**
    ```zsh
    nano ~/.zshrc
    ```

2.  **Add these lines to the very bottom of the file:**
    (Use your arrow keys to scroll down, then copy/paste this block exactly as is)

    ```zsh
    # --- GEMINI CONFIGURATION ---

    # 1. Force use of Gemini 3.1 Pro Preview (Best for Coding/Reasoning)
    export GEMINI_MODEL="gemini-3.1-pro-preview"

    # 2. Add Gemini to your system PATH
    export PATH="$HOME/.gemini/bin:$PATH"

    # 3. Shortcuts to sync skills
    # Type 'skills-push' to save new skills to GitHub
    alias skills-push="cd ~/.gemini/skills && git add . && git commit -m 'Update skills' && git push"
    
    # Type 'skills-pull' to download updates from GitHub
    alias skills-pull="cd ~/.gemini/skills && git pull"
    ```

3.  **Save and Exit:**
    * Press `Ctrl + O` then `Enter` (to Save).
    * Press `Ctrl + X` (to Exit).

4.  **Reload settings:**
    ```zsh
    source ~/.zshrc
    ```

---

## 💡 Part 3: How to Use

Simply type `gemini` in your terminal to start chatting. The AI will automatically detect when to use a specific skill based on your keywords.

### 🛠️ DevOps Engineer Skill
* **Triggers:** Azure, Terraform, Pipelines, vSphere, Ansible, Windows Server.
* **Capabilities:**
    * Validates Azure DevOps YAML pipelines (strict mode).
    * Enforces Terraform Cloud best practices.
    * Manages vSphere resources and Ubuntu/Windows servers.
* **Example:** *"Write a Terraform config for an Azure AKS cluster."*
* **Example:** *"Debug this YAML pipeline error."*

### 🍳 Executive Chef Skill
* **Triggers:** Recipes, Cooking, Grocery Lists, Meal Prep.
* **Capabilities:**
    * Generates technique-focused recipes (Kenji López-Alt style).
    * Creates organized grocery lists sorted by aisle.
    * Filters for healthy/high-protein options.
* **Example:** *"I have chicken thighs and 30 minutes, what can I make?"*
* **Example:** *"Create a grocery list for 3 days of healthy lunches."*

---

## 🔄 Maintenance

Since this folder is linked to GitHub, you can keep your skills synced across computers.

* **Saving Changes:** If you edit a skill or add a new one, type:
  ```zsh
  skills-push
  ```
* **Getting Updates:** If you switch computers, type:
  ```zsh
  skills-pull
  ```
