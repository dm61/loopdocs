# Build Errors

There are two types of build errors that happen; yellow alerts and red alerts.  Yellow alerts will not cause a build to fail, and can generally be ignored.  Red alerts will have to be resolved before you can successfully build Loop app.

The most common cause of red alerts comes from being out of sync between the various parts of Apple's infrastructure (iOS, Xcode, Swift, watchOS, macOS) that are frequently updated.  For every update to iOS/Xcode, the volunteer Loop developers have to make changes to the underlying source code.  This takes time...so when Apple updates are pushed out, sometimes there may be a short period of time until the code is updated to match.  If you encounter a build error that is not listed below, please get on the Facebook Looped group or Gitter to let us know.

## Yellow Error Alerts
**Yellow error alerts** do not cause the build to fail, those are just warnings.  Occasionally, a Loop version may have some minor discrepencies that cause a yellow alert...but you can ignore those.

<p align="center">
<img src="../img/master-done.png" width="750">
</p>

## Red Error Alerts
**Red error alerts** will prevent Loop from building on your phone.  Please take the time to read the error message and find the solution below.

### Updated Xcode, but need to Carthage Bootstrap
Error message: "**<u>Swift Compilier Error.  Module compiled with Swift 4.0 cannot be imported in Swift 4.0.x</u>**"
<p align="center">
<img src="../img/xcode9_1.png" width="750">
</p>

Soultion: Xcode was recently updated, and the current Loop master branch will produce this error message until the code is updated.  You will need to perform the following steps:

* Close Xcode
* Open Terminal App
* Navigate to your Loop download by doing the command:
`cd downloads/Loop-master`
(or whatever you named your Loop folder...go check)
* Now use the command
`carthage bootstrap`
It will run for about 4-5 minutes and then show you a screen like below.
<p align="center">
<img src="../img/carthage-bootstrap.png" width="750">
</p>

!!!info ""
    If during the run of `carthage bootstrap`, you instead see an error message like below:
    </p>
    <p align="center">
    <img src="../img/exit-code-72.jpg" width="550">
    </p>
    Please go to your Xcode preferences, under the Locations tab, select `Xcode 9.2` under the Command Line Tools
    <p align="center">
    <img src="../img/command-line-tools.png" width="750">
    </p>

    If Xcode 9.2 is not available in the dropdown menu, (1) make sure you have update your Xcode from the App store and then (2) go to Terminal app and run the command `xcode-select --install` which will produce a pop-up window for the installation of command line developer tools.  Select  `install` in that pop-up window.

    Return to Terminal app and rerun `carthage bootstrap` in your Loop download folder.  It should resolve correctly after that.
* Reopen your Loop project in Xcode, select your iPhone, and press the build button. You'll still see some yellow alerts, but those are fine.
<p align="center">
<img src="../img/yellow-update.png" width="750">
</p>

### Keychain Access

Error message: "**<u>Command /bin/sh failed with exit code 1</u>**"

</p>
<p align="center">
<img src="../img/keychain1.jpg" width="550">
</p>

</p>
<p align="center">
<img src="../img/keychain2.jpg" width="350">
</p>

Solution:  This error message has been more frequent lately, but I am unsure if there is a new underlying change in Xcode or people are inadvertently saying "no" to allowing Keychain Access. Regardless the solution is as follows:

1. Close Xcode
2. Open your Keychain Access application (found in Applications within the Utilities folder, similar to where Terminal app is found)
3. In the upper left corner of keychain access, make sure you have the keychain `login` highlighted and then click the large lock icon above the keychains area.  Click the lock closed, and then click the lock to open it again. You will be prompted for a password.  Enter your computer admin password.  Close Keychain Access app.
</p>
<p align="center">
<img src="../img/keychain3.png" width="350">
</p>
4. Open your Loop project again in Xcode.
5. In the main Xcode ribbon menu (grey menu bar at the very top of your Apple display area), select the word `Product` and then select the option for `Clean`. (keyboard shortcut is shift-command-k)
6. Now try rebuilding your Loop app.  If you ever get prompted again to allow Xcode access to Keychain, make sure to Always Allow.

### Developer License Update
Error message: "**<u>The Apple Developer Program License Agreement has been updated,  In order to access certain membership resources, you must accept the latest license agreement.</u>**"

Solution: You'll need to log onto your developer account at [developer.apple.com](https://developer.apple.com/account/) and accept the latest license agreement.
<p align="center">
<img src="../img/license.png" width="750">
</p>

### Out of Date Xcode
Error message: **<u>Swift Language Version” (SWIFT_VERSION) is required to be configured correctly</u>** for targets which use Swift. Use the [Edit > Convert > To Current Swift Syntax…] menu to choose a Swift version or use the Build Settings editor to configure the build setting directly" or also **"Could not locate device support files.  This iPhone is running iOS 11.x, which may not be supported by this version of Xcode.**"

Solution: You will need to go to your computer's App Store and install the Xcode app update.
<p align="center">
<img src="../img/old_xcode.jpg" width="750">
</p>
<p align="center">
<img src="../img/old_xcode2.jpg" width="750">
</p>
<p align="center">
<img src="../img/update.jpg" width="750">
</p>

### Bundle ID error
Error message: "**<u>Embedded Binary Validation Utility.  error: Embedded binary's bundle identifier is not prefixed with the parent app's bundle identifier</u>**".
<p align="center">
<img src="../img/bundle_fail.jpg" width="750">
</p>
Solution:  This error happens because you've either

1. Forgotten to save project after the MAIN_APP_BUNDLE_ID was changed (most common cause)
2. Tried to manually change one of the Bundle ID names in one of the four targets, or
3. Used an incorrect syntax in the MAIN_APP_BUNDLE_ID.

In any case however, usually this error is most easily solved by closing out your project, deleting the download folder, and starting with a fresh download of Loop app.  The next time you build, make sure to follow the directions carefully to use a MAIN_APP_BUNDLE_ID in the right format and press `command-s` to force Xcode to update the targets' naming scheme correction.

### Bad Source Code Folder
Error message: "**<u>Abort with payload</u>**"  Your app will only open briefly with a white screen and then close, if you build with this error.
<p align="center">
<img src="../img/abort_payload.png" width="750">
</p>
Solution: This error message is caused by either

1. Saving Loop download folder into an iCloud mapped drive, or
2. Having a space in the name of your Loop download folder.

Rename the folder to have no spaces and/or move it back to the Downloads folder, then rebuild.

### Carthage installation
Error message: "**<u>Shell Script Invocation Error.  Command /bin/sh failed with exit code 127</u>**"
<p align="center">
<img src="../img/exit127.jpg" width="250">
</p>

Solution: This error code is happening for Loopers updating to Loop who used carthage.pkg and don't have homebrew installed.  We have since updated the installation docs, so new users likely won't run into this error.  But, if you are an existing Looper encountering this error message while trying to update your Loop, please open your Terminal app found in the Applications>>Utilities folder and then enter `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`  Confirm installation by pressing enter, and then typing in your computer password.  When the installation finishes, use the command `brew link --overwrite carthage`.  After those two steps, you can close out Terminal app, return to Xcode and press the build/play button again.

### Apple Watch issues
Error: **<u>Apple watch app is not appearing</u>**.

Solution: Usually because you have not updated to watchOS 4 prior to when you built Loop, or you didn't have your Apple watch paired at the time of building Loop.  Don't forget to open the iPhone's Watch app, select My Watch tab on the bottom left, scroll all the way down, and click `Install` for the Loop app listed at the very bottom under "available apps".
