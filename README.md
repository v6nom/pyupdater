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

if __name__ == "__
