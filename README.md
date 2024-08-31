# Prelude
This is a step-by-step tutorial for those of you who only want to use Fika for PERFORMANCE, and coop is only optional. I will NOT cover how to set up for multiplayer.

I will include both a tutorial for _WAN_ and for _LAN_ setups

Feel free to skip to your preferred parts via the `Navigation hub`



# Navigation hub
- [Skip to Prequisites for LAN](https://github.com/minihazel/FIKA-FPS/main/README.md#prerequisites-lan)
- [Skip to Prequisites for WAN](https://github.com/minihazel/FIKA-FPS/main/README.md#prerequisites-wan)
- [Skip to How To Play](https://github.com/minihazel/FIKA-FPS/main/README.md#how-to-play)


# Prerequisites [LAN]
- [Download the Fika plugin (select latest version)](https://github.com/project-fika/Fika-Plugin/releases)
- [Download the Fika server (select latest version)](https://github.com/project-fika/Fika-Server/releases)
- [Download the Fika Dedicated Client plugin (select latest version)](https://github.com/project-fika/Fika-Dedicated/releases)



### Network Rules
Follow these steps on BOTH the Client PC _and_ Server PC to be safe.

Open your Windows Firewall Advanced Security app

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/brave_uSdxZUXkdB.png">

Select `Inbound Rules`

Click `New Rule...`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/mmc_mtr8EMZnfQ.png" width="600" height="400">

1. Check `Program`, click Next
2. Select your `EscapeFromTarkov.exe` in your SPT install folder, click Next
3. Check `Allow the connection`, click Next
4. Click Next
5. Set name as `EFTInbound`, click Finish
6. Repeat steps 1 to 5 for `SPT.Server.exe`. Call it `SPTInbound`

Select `Outbound Rules`

Click `New Rule...`

Repeat steps 1 - 6 from the previous segment

Call the rules `EFTOutbound` and `SPTOutbound` respectively

The path to them should be the same as for the Inbound rules



# Server PC Setup [LAN]
- Install the Fika plugin into your SPT install folder by dragging and dropping the `BepInEx` folder into it
- Install the Fika Server mod into your SPT install folder by dragging and dropping the `user` folder into it
- Install the Fika Dedicated Client plugin into your SPT install folder by dragging and dropping the `BepInEx` folder into it

Run `SPT.Server.exe` to let it generate configuration files, then close it after the `Started the webserver` text appears

Run `cmd.exe` (Command Prompt) and insert `ipconfig` to find your local IPv4

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/cmd_X7kL1mG6ZL.png">

Copy the IPv4 address. Mine is `172.16.5.4`

Navigate to `/SPT_Data/configs/configs/http.json`

Open `http.json` in your preferred text editor

- Change `ip` to `0.0.0.0`
- Change `backendIp` to your local IPv4 which you copied

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/AnyDesk_0DsbrCZSzR.png">

Navigate to `/user/mods/fika-server/assets/configs`

Open `fika.jsonc`

Scroll down to the `dedicated` section

- Change `"amount"` to `1`.
- Change `"forceIp"` to `127.0.0.1`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/AnyDesk_4l6tm7Q2tR.png">

Start your SPT Server. The `Started webserver` text should now specify your IPv4

Close your server

Navigate to `/user/mods/fika-server/assets/scripts`

You should now have a batch (`.bat`) script that starts with `Start_dedicated_xxxxxx`

Copy/move this file to your SPT install folder (where `SPT.Server.exe` is)

### ⚠️ Every time you finish a raid, you must CLOSE the BepInEx game console on the Server PC and run the `Start_dedicated_xxxxxx` script again ⚠️



# Client PC Setup [LAN]
Install the Fika Plugin mod into your SPT install folder by dragging and dropping the `BepInEx` folder into it.

Run `SPT.Launcher.exe`

Open `Settings`

Check `Developer Mode`

Find your Server PC's IPv4 from earlier. We'll call mine `ServerPCPort`

Set the URL to `http://ServerPCPort:6969`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/SPT.Launcher_MWmXxvDHLV.png" width="600" height="400">

Hit Enter, then close the launcher.

When the Server PC Server + Dedicated Client are both running, run `SPT.Launcher.exe` and log in with a new/existing username.



# Server PC Setup [WAN]
- Install the Fika plugin into your SPT install folder by dragging and dropping the `BepInEx` folder into it
- Install the Fika Server mod into your SPT install folder by dragging and dropping the `user` folder into it
- Install the Fika Dedicated Client plugin into your SPT install folder by dragging and dropping the `BepInEx` folder into it

Run `SPT.Server.exe` to let it generate configuration files, then close it after the `Started the webserver` text appears

Get your public WAN IP address. Find it here: [ICanHazIP](https://ipv4.icanhazip.com/)

Navigate to `/SPT_Data/configs/configs/http.json`

Open `http.json` in your preferred text editor

- Change `ip` to your WAN IP address
- Change `backendIp` to your WAN IP address

Navigate to `/user/mods/fika-server/assets/configs`

Open `fika.jsonc`

Scroll down to the `dedicated` section

- Change `"amount"` to `1`.
- Change `"forceIp"` to `127.0.0.1`

Start your SPT Server. The `Started webserver` text should now specify your WAN IP address

Close your server

Navigate to `/user/mods/fika-server/assets/scripts`

You should now have a batch (`.bat`) script that starts with `Start_dedicated_xxxxxx`

Copy/move this file to your SPT install folder (where `SPT.Server.exe` is)

### ⚠️ Every time you finish a raid, you must CLOSE the BepInEx game console on the Server PC and run the `Start_dedicated_xxxxxx` script again ⚠️



# Client PC Setup [WAN]
Install the Fika Plugin mod into your SPT install folder by dragging and dropping the `BepInEx` folder into it.

Run `SPT.Launcher.exe`

Open `Settings`

Check `Developer Mode`

Find your Server PC's WAN IP address from earlier. We'll call mine `WANAddress`

Set the URL to `http://WANAddress:6969`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/SPT.Launcher_MWmXxvDHLV.png" width="600" height="400">

Hit Enter, then close the launcher.

When the Server PC Server + Dedicated Client are both running, run `SPT.Launcher.exe` and log in with a new/existing username.
