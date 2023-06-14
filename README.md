# installmacos
I always seem to forget how to download the macOS version I need by the time I need it again, so here is a quick and nasty guide on how to download a properly signed `*.dmg` file to build a USB installer.

* The script below is just copy pasted from here: https://github.com/grahampugh/macadmin-scripts (This is a jacked up version of the original found here: https://github.com/munki/macadmin-scripts)
* Here is some nice documentation to use the script: https://derflounder.wordpress.com/2018/02/27/using-installinstallmacos-py-to-download-macos-high-sierra-installers/
* I've found that they are not reliable in all situations, especially on newer versions of MacOS. The version I've commited here works everytime in my testing

If you don't want to download the tool or monkey around with permissions, give this a shot: (Provided you are dumb enough to pipe unknown code off the internet in `sudo python` of course):

* `sudo curl -s https://raw.githubusercontent.com/boerso/installmacos/master/installinstallmacos.py | sudo python -`

If you're downloading an installer for your current machine, do the following:

1. Run `sudo curl -s https://raw.githubusercontent.com/boerso/installmacos/master/installinstallmacos.py | sudo python3 -`
2. Copy the build number of the macOS version you want to download
3. Run `sudo curl -s https://raw.githubusercontent.com/boerso/installmacos/master/installinstallmacos.py | sudo python3 - --workdir ~/Downloads --build build_version`
4. Open your Downloads directory after the download is complete, and you should be in business

To create a bootable USB installer, do the following:

1. Plug in the USB drive you want to use as the installer
2. Run `ls -la /Volumes`
3. Copy the full path to the mounted USB volume (e.g. `/Volumes/Untitled`)
4. Run `/Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /path/to/mounted/volume`
5. Accept all the prompts, wait a long time, and you're done
