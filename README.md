# DISCLAIMER!
### Support queries will be invalidated if you follow this tutorial. If you need FIKA support, follow THEIR instructions.

Fika Discord link: [discord.gg/project-fika](https://discord.gg/project-fika)

If you prefer a video tutorial, step-by-step, at a slow pace: [Installing Fika for Performance](https://www.youtube.com/watch?v=VmyaSjbZelg)

NOTE: The video tutorial IS OUT OF DATE. If you use common sense, it should work. If you need careful instructions, do not watch the video tutorial.

# Prelude
This is a step-by-step tutorial for those of you who only want to use Fika for PERFORMANCE, and coop is only optional. I will NOT cover how to set up for multiplayer.

I will include both a tutorial for _WAN_ and for _LAN_ setups

Feel free to skip to your preferred parts via the `Navigation hub`

## Important note

### Make sure you have run the game (and made it to the main menu) on BOTH the Server and Client machines.

LAN is for closed networks, where both Server and Player are machines on the same network/WiFi.

WAN is for the whole world, where Server and Player are machines on separate networks/WiFi.

When your setup is done, you should have TWO (2) separate folders.

- One (1) folder for the Server + Headless Client.
- One (1) folder for the Player.

## Important note #2

The process and setup is the same whether you are installing everything on the same machine, or using two different machines.

Follow the instructions and you will be fine.



# Navigation hub
Read these sections one by one, top to bottom (choose whether you want WAN or LAN setup)

- [Prequisites](https://github.com/minihazel/FIKA-FPS#prerequisites)
- [How To Play](https://github.com/minihazel/FIKA-FPS#how-to-play)
- [Server PC tips for additional performance](https://github.com/minihazel/FIKA-FPS#additional-tips)

### WAN related
- [Server PC Setup for WAN](https://github.com/minihazel/FIKA-FPS#server-pc-setup-wan)
- [Player PC Setup for WAN](https://github.com/minihazel/FIKA-FPS#client-pc-setup-wan)

### LAN related
- [Server PC Setup for LAN](https://github.com/minihazel/FIKA-FPS#server-pc-setup-lan)
- [Player PC Setup for LAN](https://github.com/minihazel/FIKA-FPS#client-pc-setup-lan)


# Prerequisites

### IF YOU WISH TO PLAY WITH A VPN, REFER TO FIKA'S GUIDE FOR HOSTING VIA VPN: [Host using a VPN](https://github.com/project-fika/fika-documentation?tab=readme-ov-file#host-using-a-vpn)

Guide on how to set up port forwarding [WAN]: [Beginners Guide to Port Forwarding](https://www.youtube.com/watch?v=jfSLxs40sIw)

- [Download the Fika plugin (select latest version)](https://github.com/project-fika/Fika-Plugin/releases)
- [Download the Fika server (select latest version)](https://github.com/project-fika/Fika-Server/releases)
- [Download the Fika Headless Client plugin (select latest version)](https://github.com/project-fika/Fika-Headless/releases)



### Network Rules
Follow these steps on BOTH the Player PC _and_ Server PC to be safe.

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
- Install the Fika Headless Client plugin into your SPT install folder by dragging and dropping the `BepInEx` folder into it

Run `SPT.Server.exe` to let it generate configuration files, then close it after the `Started the webserver` text appears

Run `cmd.exe` (Command Prompt) (or Windows Terminal) and insert `ipconfig` to find your local IPv4

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/WindowsTerminal_gtvUD5Kvys.png">

Copy the IPv4 address. Mine is `192.168.1.116`

Navigate to `/user/mods/fika-server/assets/configs`

Open `fika.jsonc`.

(If you cannot find `fika.jsonc`, run `SPT.Server.exe`, wait until you see `Started the webserver` text, then try again)

Scroll down to the `server` section

- Change `"backendIp"` to your IPv4 address, mine is `192.168.1.116`.
- Change `"ip"` to `0.0.0.0` if it isn't already.

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/VSCodium_nTsdm24RcX.png">

Scroll down to the `headless` section

- Change `"amount"` to `1`.
- Change `"forceIp"` to `127.0.0.1`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/notepad%2B%2B_AxvecGmdTi.png">

Start your SPT Server. The `Started webserver` text should now specify your IPv4

Close your server

Navigate to `/user/mods/fika-server/assets/scripts`

You should now have a Powershell (`.ps1`) script that starts with `Start_headless_xxxxxx`

Copy/move this file to your SPT install folder (where `SPT.Server.exe` is)



# Client PC Setup [LAN]
Install the Fika Plugin mod into your SPT install folder by dragging and dropping the `BepInEx` folder into it.

Run `SPT.Launcher.exe`

Open `Settings`

Check `Developer Mode`

Find your Server PC's IPv4 from earlier. We'll call mine `ServerPCPort`

Set the URL to `http://ServerPCPort:6969`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/SPT.Launcher_MWmXxvDHLV.png" width="600" height="400">

Hit Enter, then close the launcher.

When the Server PC Server + Headless Client are both running, run `SPT.Launcher.exe` and log in with a new/existing username.



# Server PC Setup [WAN]
- Install the Fika plugin into your SPT install folder by dragging and dropping the `BepInEx` folder into it
- Install the Fika Server mod into your SPT install folder by dragging and dropping the `user` folder into it
- Install the Fika Headless Client plugin into your SPT install folder by dragging and dropping the `BepInEx` folder into it

Run `SPT.Server.exe` to let it generate configuration files, then close it after the `Started the webserver` text appears

Get your public WAN IP address. Find it here: [ICanHazIP](https://ipv4.icanhazip.com/)

Navigate to `/user/mods/fika-server/assets/configs`

Open `fika.jsonc`.

(If you cannot find `fika.jsonc`, run `SPT.Server.exe`, wait until you see `Started the webserver` text, then try again)

Scroll down to the `server` section

- Change `"ip"` to your WAN IP address.
- Change `"backendIp"` to WAN IP address.

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/VSCodium_nTsdm24RcX.png">

Scroll down to the `headless` section

- Change `"amount"` to `1`.
- Change `"forceIp"` to `127.0.0.1`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/notepad%2B%2B_AxvecGmdTi.png">

Start your SPT Server. The `Started webserver` text should now specify your WAN IP address

Close your server

Navigate to `/user/mods/fika-server/assets/scripts`

You should now have a Powershell (`.ps1`) script that starts with `Start_headless_xxxxxx`

Copy/move this file to your SPT install folder (where `SPT.Server.exe` is)



# Client PC Setup [WAN]
Install the Fika Plugin mod into your SPT install folder by dragging and dropping the `BepInEx` folder into it.

Run `SPT.Launcher.exe`

Open `Settings`

Check `Developer Mode`

Find your Server PC's WAN IP address from earlier. We'll call mine `WANAddress`

Set the URL to `http://WANAddress:6969`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/SPT.Launcher_MWmXxvDHLV.png" width="600" height="400">

Hit Enter, then close the launcher.

When the Server PC Server + Headless Client are both running, run `SPT.Launcher.exe` and log in with a new/existing username.



# How To Play
Now that everything is set up, it's time to play!

### Server PC
Run `SPT.Server.exe`

Wait for the `Started webserver` text to appear

Right-Click the `Start_headless_xxxxxx.ps1` Powershell script that is in your SPT install folder.

Click `Run with Powershell`. There will be a 3 or 5 second wait period.

Wait until both consoles have stopped spamming.

### Client PC
⚠️ Make sure the Server PC has been set up for the server to allow the connection ⚠️

Run `SPT.Launcher.exe`

Wait for the UI to update and connect you to the login page

Make a new account, log in to an existing one, or play game.

Once in-game, begin the process by selecting the map you want to play on.

Click next until you pass the Insurance screen.

Next, click `HOST RAID`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/EscapeFromTarkov_R1KTixNMV1.jpg" width="600" height="350">

Check `Use Headless Host`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/EscapeFromTarkov_pODLB2a1V5.png" width="600" height="450">

Click `START`

Now wait. You should soon be in raid.



# Additional tips
For those of you who want to squeeze that extra juice out of your already hopefully more performant setup, here are a few things you can do to alleviate some of it.

### Process Lasso for CPU (mainly Intel CPUs)
1. On your Client PC, download [Process Lasso](https://bitsum.com/download-process-lasso/)
2. Install it
3. Run the SPT Server, then run the SPT Launcher
4. Log into any account available on the server
5. Once in-game, run Process Lasso
6. Go to `Active processes` (go to `All processes` to search if you cannot find the game there)
7. Select `EscapeFromTarkov.exe`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/AnyDesk_WTfO6dHL52.png">

1. Right-click it
2. Go to `CPU Priority` -> `Always` -> Set it to `High`

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/AnyDesk_LkAO3YJeR1.png">

1. Right click it again
2. Go to `CPU Affinity` -> `Always` -> `Select CPU Affinity`
3. Uncheck all checkboxes
4. Check CPU core 1-4 (or 1-6 if you have that many)

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/AnyDesk_4Q0iGVQhQD.png">



### Boot.config
1. On your Server PC, navigate to `/EscapeFromTarkov_Data`
2. Open `boot.config`
3. Add `job-worker-count=` to the end of the file, if you haven't already.
4. At the end of the line you just added, add the number of your threads - 1.

<img src="https://github.com/minihazel/FIKA-FPS/blob/main/notepad++_YZ6PyyxC4M.png">

### Client mods for CPU help
These are client mods you can install on your Client PC to hopefully alleviate some strain.

- ~~[De-Clutterer](https://hub.sp-tarkov.com/files/file/1785-de-clutterer-updated-by-cj/) (recommended value: `2.0`)~~ This mod is no longer available for 3.11, whether it will return in a functional state is unclear.
- [Amand's Graphics](https://hub.sp-tarkov.com/files/file/813-amands-s-graphics/)
- [RamCleanerInterval](https://hub.sp-tarkov.com/files/file/1827-ram-cleaner-fix/) (install this on your Server PC SPT install *as well*, just in case)
