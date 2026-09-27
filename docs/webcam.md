# Webcam

While PrismDesk is running, the camera of the connected device shows up on the
PC as an ordinary Windows camera called **PrismDesk Camera**. Any app that lists
cameras can pick it.

## Turning it on

1. On the PC, open the host window → **Settings** → **Virtual camera**, and turn
   on *Publish the camera of the device as a Windows virtual camera*.
   The same section shows **Virtual camera: registered with Windows** once it is
   there.
2. On the device, connect as usual, then swipe left from the handle at the
   right edge of the picture for the control menu, and tap **Camera**.
3. In the app on the PC, choose **PrismDesk Camera**.

**The camera exists only while PrismDesk is running on the PC.** Stopping the
host removes the device from Windows; starting it puts it back.

## Where each setting lives

| | |
|---|---|
| **What the device captures** (resolution, frame rate) | The Android app: Settings → Camera. Only what the camera actually reports is offered. |
| **What Windows is offered** (the resolution and frame rate other apps see) | The host window: Settings → Virtual camera → *Output resolution*. |

Raising the capture side above what the host puts out only costs data and heat.
Applying a new output resolution recreates the camera, so apps that were using
it have to select it again.

**Front and rear** are switched from the same control menu — **Front** /
**Rear**. The orientation of the picture follows the device by itself.

Using the device as a second monitor and as a camera at the same time works.

## Verified

- Windows **Camera** app — the picture is there, which is the quickest way to
  check the camera at all.
- **Discord** — works.

Other apps are expected to work the same way (it is a normal Media Foundation
camera), but those are the two that have been tried.

## The rear camera looks mirrored in Discord

**That is Discord, not PrismDesk.** Discord mirrors your own self-view; the
front camera looks mirrored for the same reason, and that is the giveaway.
Nothing in the path flips the picture — front and rear both go out unmirrored,
and that is what the person on the other end receives.

To check for yourself: open the Windows **Camera** app, select *PrismDesk
Camera*, and point the rear camera at some text. If you can read it, the picture
on the wire is the right way round.

We do not mirror it at the source, because that would send everyone else a
backwards picture.

## "PrismDesk Camera" is not in the list

- **Is the host running?** The camera only exists while it is.
- **Is the virtual camera turned on?** The host window's Settings tab says
  *registered with Windows*, *not registered*, or *off*.
- **Was the app already open?** Apps enumerate cameras when they start. Close it
  and open it again.
- **Something else on the PC can block the registration.** We have seen a case
  where another program on the machine kept the virtual camera from being
  registered. If the host says it is on but Windows never lists it, that is the
  direction to look — and please
  [open an issue](https://github.com/Asynchronous-0x4C/prismdesk-app/issues/new/choose) so it can go on this page by name.

## Photos will not save (`0xA00F424F` / `0x80270200`)

**This one is not PrismDesk.** If the Windows **Camera** app fails to save a
photo with `0xA00F424F <PhotoCaptureFileCreationFailed> (0x80270200)`, the second
code is Windows' `LIBRARY_E_NO_SAVE_LOCATION` — *the library has nowhere to
save*. **It happens with no camera involved at all**; it only looks like a
PrismDesk problem because you were using our camera when you hit it.

It turns up on PCs whose user profile was carried over from another PC or
another account: the library definitions still point at the previous user, while
the folder itself and its permissions are perfectly fine.

**The fix:** in File Explorer, right-click **Libraries** in the navigation pane
and choose **Restore default libraries**. (If *Libraries* is not shown: View →
Navigation pane → Show libraries.) We have confirmed on a real machine that
saving works again immediately afterwards.

If some libraries still fail, open the properties of that one library and use
**Restore Defaults** — restoring the defaults does not rebuild a library you had
added locations to.

Video itself — the preview, Discord, anything else — is unaffected by this
error.

## A camera app stops responding after the host is stopped or started

**Close the camera app before you stop or start the host.** The PrismDesk
camera lives and dies with the host, so stopping the host removes the camera
device from Windows, and an app that is still holding it may not cope. On a real
machine the Windows Camera app had to be forced to close. Changing the output
resolution in the host window does the same thing.

Open the app again and select the camera again, and it comes back. How other
apps behave in this situation has not been measured.

See also: [Known issues](known-issues.md) · [FAQ](faq.md)
