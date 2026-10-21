---
icon: lucide/hammer
---

# Build your first iOS app on Linux / Windows

Once you've completed the Installation steps, you can use **xtool** to build and deploy an iOS app directly from your Linux or Windows machine.

*Estimated Time: 15 mins*

## 1. Create an xtool project

We'll start by creating a project from xtool's default template. xtool comes with a template for iOS-capable Swift Packages.

Open your terminal and run the following command to create a new package named `Hello`:

```bash
xtool new Hello
```

At this point, feel free to poke around. Observe that the package is structured a lot like a regular SwiftPM library, with a few extra files:

* **`xtool.yml`**: This file describes how to bundle the Swift library into an iOS app. At a minimum, you need to provide a Bundle ID. This defaults to `com.example.<PackageName>` (in this case, `com.example.Hello`).

* **`.bsp/xtool.json`**: This file tells your IDE to ask xtool for build information (via the Build Server Protocol). It enables features like syntax highlighting and documentation lookup.

## 2. Build and run

Now that we have a skeleton project, let's get it running on your device. Navigate inside your new project directory and launch the dev server:

```bash
cd Hello
xtool dev
```

!!! info "First Build Time"
    The first time you run this, SwiftPM might take a few minutes to build the app because it needs to build the Swift Modules for the iOS SDK. Subsequent runs will be much faster since SwiftPM caches these modules globally.

### Device Installation Steps

After the build is complete, xtool will attempt to install it on your device. Connect your iOS device to your computer via USB.

*(If you installed `libimobiledevice-utils` during setup, you can verify that your device is connected by running `ideviceinfo`).*

xtool will handle the rest, but you may need to complete a few steps on your iPhone/iPad the first time:

!!! warning "1. Pair your device"
    You may see a **"Trust This Computer?"** dialog on your iOS device. Tap **Trust** and enter your passcode. If xtool throws an error after this, just run `xtool dev` again.

!!! warning "2. Enable Developer Mode"
    You may run into an error asking you to enable **Developer Mode**. On your iOS device, go to *Settings > Privacy & Security > Developer Mode* and turn it on. Your device will restart. Run `xtool dev` again afterwards.

!!! warning "3. Trust the Developer"
    xtool generates a Certificate and App ID to sign the app. The first time you tap the app on your home screen, you will get an **"Untrusted Developer"** alert.
    To fix this: Go to *Settings > General > VPN & Device Management > [your Apple ID email]* and tap **Trust**.

You should now be able to launch the "Hello" app on your device!