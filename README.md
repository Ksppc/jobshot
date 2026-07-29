# Cove

A camera that files itself.

Every shot is stamped with its job number, location and timestamp, then uploaded
straight into the right job folder on Google Drive — no sorting afterwards, no
photos left stranded in a camera roll.

## How it works

- **Pick a job once.** The folder picker opens inside the production photo folder
  and shows only the job folders in it. The folder name becomes the Job#, and a
  code like `PPC-2026-056` is detected automatically.
- **Shoot.** The job number, location and date/time are burned into the image
  itself, so the photo still carries its own record if it is ever copied,
  emailed or pulled into a report.
- **It uploads itself.** Straight to the chosen folder, named
  `{Job#}_{date}_{time}.jpg`.

Sign-in is once per device. The session is cached and renewed silently, so the
Google consent screen only returns if access is revoked, the device signs out of
Google, or site data is cleared.

## Configuration

Both live at the top of `index.html`:

| Constant | Purpose |
| --- | --- |
| `ROOT_FOLDER_ID` | The Drive folder the picker is pinned to. Only folders inside it can be chosen. |
| `CONFIG_VERSION` | Bump it to force every device to re-pick its folder — used when the root moves. |

Location and watermark logo are set per device under Settings.

## Install

It is a PWA. Open the page on the phone and use *Add to Home Screen*; it then
launches full-screen with its own icon.
