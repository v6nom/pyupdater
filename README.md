<p align="center">🛠️ PyUpdater Auto-Update Guide 🛠️</p>
<br><br>

<p align="center"><strong>This repository demonstrates how to use PyUpdater to add auto-update functionality to your Python application.<br><br>By following this guide, you will be able to distribute and update your Python programs efficiently.</strong></p>
<br>

<p align="center">📦 Example Python Scripts 📦</p>
<p align="center"><strong><i>Here are some example scripts to demonstrate the implementation of PyUpdater.</i></strong></p>
<br><br>

<p align="center">basic_script.py</p>
<p align="center"><strong><i>This is a simple Python script that implements a basic auto-update feature using PyUpdater.</i></strong></p>

<pre>
<code>
from pyupdater.client import Client

APP_NAME = "MyApp"
APP_VERSION = "1.0.0"

def update():
    client = Client(ClientConfig(), refresh=True)
    client.add_progress_hook(print_progress_info)
    if client.update_check(APP_NAME, APP_VERSION):
        print("New version available!")
        client.download()
        client.extract_restart()
    else:
        print("No update available.")

def print_progress_info(info):
    print(f"{info.get('percent_complete', 0)}% complete")

if __name__ == "__main__":
    update()
</code>
</pre>
<br><br>

<p align="center">🛠️ How to Integrate PyUpdater 🛠️</p>
<br><br>

<p align="center"><strong><i>Follow these steps to add auto-update functionality to your Python application using PyUpdater:</i></strong></p>
<br><br>

<h3>Step 1: Install PyUpdater and Dependencies</h3>

<ol>
  <li>Install PyUpdater via pip:
    <pre><code>pip install pyupdater</code></pre>
  </li>
  
  <li>Install other dependencies (e.g., PyInstaller for packaging):
    <pre><code>pip install pyinstaller</code></pre>
  </li>
</ol>

<h3>Step 2: Configure PyUpdater</h3>

<ol>
  <li>Create a configuration file <code>client_config.py</code>:
    <pre><code>from pyupdater.client import ClientConfig

class ClientConfig(ClientConfig):
    PUBLIC_KEY = "your_public_key"
    COMPANY_NAME = "your_company_name"
    APP_NAME = "MyApp"
    UPDATE_URLS = ["https://your-update-server.com/updates/"]
</code></pre>
  </li>

  <li>Set up your server to host the update files (this could be an FTP server, AWS S3, etc.).</li>
</ol>

<h3>Step 3: Package Your Application</h3>

<ol>
  <li>Use PyInstaller or any other packaging tool to compile your Python script into an executable:
    <pre><code>pyinstaller --onefile --name=my_app your_script.py</code></pre>
  </li>
  
  <li>Generate the update files with PyUpdater:
    <pre><code>pyupdater pkg -n MyApp -v 1.0.0</code></pre>
  </li>

  <li>Deploy the update files to your update server.</li>
</ol>

<h3>Step 4: Integrate the Update Functionality</h3>

<p>In your Python script, use the PyUpdater Client to check for updates and download them if available. Refer to the <code>basic_script.py</code> example provided earlier.</p>

<br><br>

<p align="center">🔄 How Auto-Update Works 🔄</p>
<br><br>

<p>When your application starts, it will check with the update server to see if a newer version is available. If an update is found, it will download and apply it automatically, ensuring your users always have the latest version.</p>

<br><br>

<p align="center">🗂️ Additional Resources 🗂️</p>
<br><br>

<p>For more detailed instructions on configuring and using PyUpdater, check out the official documentation:</p>

<p align="center"><a href="https://pyupdater.readthedocs.io/en/latest/">PyUpdater Documentation</a></p>

<br><br>

<p align="center">README.md inspired by <a href="https://github.com/billythegoat356/">this repo</a></p>
