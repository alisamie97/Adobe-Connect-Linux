# Unofficial Adobe Connect Client for Linux
## Description:
Adobe Connect does not have a linux version officially, however, since it's written in flash, it's possible to run it in a browser. This project, uses an underlying chromium browser with flash support to run the flash file behind the meetings. It provides the binding necessary to automatically launch the app just like the Windows version for convenience.
This project uses [Chromium Embedded Framework](https://github.com/chromiumembedded) to utlize the underlying browser
## Installation
- To install the app, either [build from source](#building-from-source) or [download a prebuilt binary from the Releases section](https://github.com/mahancoder/Adobe-Connect-Linux/releases)

- After that, you need to get `libpepflashplayer.so`. Due to copyright reasons, I can't provide it here.
You can get it from the [archive.org copy of the official Adobe Pepper Flash Player](https://web.archive.org/web/20210101005931/https://fpdownload.adobe.com/pub/flashplayer/pdc/32.0.0.465/flash_player_ppapi_linux.x86_64.tar.gz)

- Extract the archive. The file you need is `libpepflashplayer.so`.

- Then, you need to unlock it using this tool [darktohka/FlashPatch](https://github.com/darktohka/FlashPatch).

- After that, put the patched `libpepflashplayer.so` in `~/.local/lib/flash/` (create the flash directory if it doesn't exist)

- Now, exectue `install.sh` **as your normal user** to install the app:
    ```
    ./install.sh
    ```

### Building from source
- First clone the repository
    ```
    git clone https://github.com/mahancoder/Adobe-Connect-Linux.git
    ```
- Then run `make.sh` to generate the binaries. Refer to the installation section provided above. Note that you need to work in the `Release` folder generated by the build script and not the main clone folder.
    ```
    ./make.sh
    cd Release
    ```
## Usage
You can use the app to open meeting launched from your browser. Currently, you can't enter the meeting URL directly in the app, but rather you should enter it in the browser, and after logging in, click on the `Open in Application` button. You might also need to add `&proto=true` to the end of your meeting url. **As of right now, Screen sharing does NOT work due to how pepper flash works.**
#### **NOTE:** You NEED to change your User-Agent to be able to open the meeting. For that, you can use the User-Agent Switcher and Manager extension. [Chrome](https://chrome.google.com/webstore/detail/user-agent-switcher-and-m/bhchdcejhohfmigjafbampogmaanbfkg) and [Firefox](https://addons.mozilla.org/en-US/firefox/addon/user-agent-string-switcher/)

**As of right now, the screen sharing and file download features do not work.**
## FAQ
If the app does not open, try the following command:
```
xdg-open connectpro:https://google.com
```
If the app opens and shows the Google page, the issue is from your browser.
If not, then the error might be `gio: Operation not supported`. If that's the case, the issue can usually be solved by entering the following command:
```
xdg-mime default connect.desktop x-scheme-handler/connectpro
```
Otherwise, consider opening a new issue for further diagnosing.
## Credits
The project wouldn't be possible without the [Chromium Embedded Framework](https://github.com/chromiumembedded)

The app's icon is made by [u/arash28134](https://www.reddit.com/user/arash28134)

The orignal Adobe Connect and Adobe Flash Player are made by Adobe Inc.
