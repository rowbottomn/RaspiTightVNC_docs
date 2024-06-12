# Setting Up TightVNC on Raspberry Pi and Windows 10 PC

## 1. Install TightVNC Server on Raspberry Pi
- Update your Raspberry Pi:

```sudo apt update && sudo apt upgrade -y```

- Install TightVNC server:

```sudo apt install tightvncserver```

- Start the VNC server for initial setup:

```vncserver```

- Set a password when prompted (it will be truncated to 8 characters).

## 2. Configure VNC as a Service (Optional)
- Create a system service file:

```sudo nano /etc/systemd/system/vncserver.service```

- Add the following content BUT making sure you change the user from pi if your user has another name.
```
[Unit] Description=TightVNC Server After=network.target

[Service] Type=forking User=pi ExecStart=/usr/bin/vncserver :1 ExecStop=/usr/bin/vncserver -kill :1

[Install] WantedBy=multi-user.target
```
- Save the changes (Ctrl + X, Y, Enter).

- Run this line to start this line:
  ```sudo systemctl enable vncserver.service```

## 3. Install TightVNC Client on Windows 10 PC
- Download and install the TightVNC client from the official website.
- Choose to install only the client portion during installation.
- IMPORTANT: If you cannot install then use this link to download the installation free version, unzip and click the vncviewer.exe, then follow instructions as below.

## 4. Find Your Raspberry Pi's IP Address
- On your Raspberry Pi, run:

```ifconfig```

- Note down the IP address on the wireless network.

## 5. Connect to Your Raspberry Pi
- Open the TightVNC Viewer on your Windows PC.
- Enter your Raspberry Pi's IP address followed by the default port (5901):

example: ```172.16.120.21:5901```

- Click "Connect."
