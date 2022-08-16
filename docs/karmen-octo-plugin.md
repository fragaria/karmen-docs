# Karmen Connector - Octoprint Plugin

## Requirements
- device with Octoprint
- account on [next.karmen.tech](https://next.karmen.tech)

## Step by step setup
### Instalation of Karmen Connector plugin
Log into your octoprint like **admin** user.  
Go to Settings => Plugin Manager and choose "**GET MORE**"  
![Octoprint](_media/octo-plugin/octo-plugin-manager.png ":size=1024")

Search Karmen Connector plugin and instal  
![Octoprint](_media/octo-plugin/octo-plugin-instal.png ":size=1024")

!> Now you would be asked for rebooting your device to apply changes. Let's do it!

### Creating Karmen device key
Go to Setting => Account look for button "**Create new Device Key**"
![Octoprint](_media/own-octopi-connect-to-karmen/cloud-new-device-key1.png ":size=1024")

After pressing button you will get an unique device key.  
Highly recommend to keep this window open. Key will be used at **plugin & adding new printer**.
![Octoprint](_media/own-octopi-connect-to-karmen/cloud-new-device-key2.png ":size=1024")

## Fill key to plugin
Go to Settings => Karmen Connector plugin, fill `Device key` and save settings.
![Octoprint](_media/octo-plugin/octo-plugin-setup.png ":size=1024")

### Creating Octoprint secondary API key
!> We don't recommend using Octoprint master API key. Please for Karmen Connertor create separate API key.

Go to Setting => Application keys  
There you could name secondary key and create.  
We chose `karmenCLOUD` to easy find his purpouse in future.

![Octoprint](_media/octo-plugin/octo-secondary-api-key.png ":size=1024")

### Adding printer to your Karmen workspace
Open Setting => Printers => Add Printer button.  
Now fill information like example below.  

`Printer name` is your name of printer  
`Octoprint API Key` is secondary API we generated in Octoprint  
`Device key` is key generated to fill into plugin  
![Octoprint](_media/octo-plugin/en/en-cloud-new-printer.png ":size=1024")


# Contacts & support
We’ll gladly answer all your questions or comments. Please get in touch at karmen@karmen.tech. Thank you for your interest and support!

