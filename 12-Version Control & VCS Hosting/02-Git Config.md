---
Content: Git Configuration in VS Code
Provider: Git
Steps:
  - "[[#Open Vs Code Terminal]]"
  - "[[#Set Your Identity Globally]]"
  - "[[#Set Your Identity for One Specific Project (Optional)]]"
  - "[[#Verify the Configuration]]"
Resources:
  - "[Learn Git and Github - Elzero Web School](https://www.youtube.com/playlist?list=PLDoPjvoNmBAw4eOj58MZPakHjaO3frVMF)"
---
>To configure your username and email in Git within VS Code, open the built-in terminal and run the standard **`git config` commands**.
# 1. Open Vs Code Terminal

- Use the shortcut `Ctrl + \` `(Windows/Linux)`.
- Alternatively, click **Terminal** in the top menu and select **New Terminal**.

---
# 2. Set Your Identity Globally

This applies the username and email to **all repositories** on your computer:
- Set your name:
	`git config --global user.name "Your Name"
- Set your email:
	`git config --global user.email "your.email@example.com"`
	
>(Note: Replace `"Your Name"` and `"your.email@example.com"` with your actual details, keeping the quotation marks).

---
# 3. Set Your Identity for One Specific Project (Optional)

If you need a different profile for a single project (e.g., separating work and personal accounts), navigate to that project folder in VS Code, omit the `--global` flag, and run:
- Set local name:
	 `git config --local user.name "Your Specific Name"`
- Set local email:
	 `git config --local user.email "your.specific@email.com"`

---
# 4. Verify the Configuration

To confirm that your settings were saved correctly, run: 
	`git config --list`