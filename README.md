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

## No sign-in

There is no Google account on the phone. Photos are posted to an Apps Script
uploader that runs as the owner and files them in Drive.

The crew types a **shop PIN** once per device. It never expires. Setting up a
new hire is: hand them the phone, tell them four digits.

The device holds no Google credentials and no Drive access of any kind. The
uploader refuses to write anywhere outside the production photo folder, so the
worst a leaked PIN buys anyone is junk photos in a job folder — they cannot
read, list, move or delete a thing.

## Dead zones

A photo is written to the device *before* any upload is attempted, and is only
deleted once Drive confirms it. Lose signal, close the app, flatten the battery
— the photo is still there and goes up on the next chance.

The queue drains oldest-first and stops at the first failure, so order holds. It
retries on reconnect, when the app returns to the foreground, and every 30
seconds. A counter in the top bar shows what is waiting; tap it to force a send.

## Configuration

At the top of `index.html`:

| Constant | Purpose |
| --- | --- |
| `ROOT_FOLDER_ID` | The Drive folder the picker is pinned to. Only folders inside it can be chosen. |
| `CONFIG_VERSION` | Bump it to force every device to re-pick its folder — used when the root moves. |
| `SLOT_URL` | The Apps Script uploader. Repoint this if the script is ever redeployed to a new URL. |

The PIN lives in the Apps Script, never in this file — this repo is public.

Location and watermark logo are set per device under Settings.

## Install

It is a PWA. Open the page on the phone and use *Add to Home Screen*; it then
launches full-screen with its own icon.
