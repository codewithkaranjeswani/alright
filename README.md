# [alright](#)

My fork of [alright](https://github.com/Kalebu/alright)

### Install

```bash
conda create -n web-py311 python=3.11 -c conda-forge
conda install -c conda-forge selenium webdriver-manager platformdirs
```

### You must have alright in your dev dependency

```bash
conda develop alright
```


### Example

```python
from alright import WhatsApp
from pathlib import Path
usernames = ["WAContactName1", "WAContactName2"]
msg = "Good Morning :)"

messenger = WhatsApp()
print(messenger.__version__)
for username in usernames:
    found = messenger.find_by_username(username=username)
    if found:
        messenger.send_message(msg)
        messenger.wait_until_message_successfully_sent()
        messenger.send_file(filename=Path("/home/user/Downloads/some.pdf"), message="This is a file for you!")
        messenger.wait_until_message_successfully_sent()
        messenger.send_picture(picture=Path("/home/user/Pictures/some.png"), message="This is a picture for you!")
        messenger.wait_until_message_successfully_sent()

```
