
# Fedora ISO Download, Verification, and USB Writing Script

This script automates the process of downloading a specific version of Fedora, verifying its checksum and GPG signature, and then writing the ISO file to a specified USB device. The script includes checks to ensure all files are fully downloaded and verified before prompting the user to proceed with writing to a USB drive.

## Prerequisites

1. **Bash**: Ensure that you have Bash installed on your system.
2. **gpg**: GPG is required for signature verification.
3. **curl**: The script uses `curl` to download the necessary files.

## Usage

Run the script with the following command:
```bash
./<script_name>.sh <FEDORA_VERSION> <USB_DEVICE> [ARCHITECTURE]
```

- `<FEDORA_VERSION>`: The version of Fedora to download (e.g., `41`).
- `<USB_DEVICE>`: The path to the USB device (e.g., `/dev/sdX` or `/dev/diskX`).
- `[ARCHITECTURE]` (optional): The system architecture to download. Defaults to `x86_64` if not specified.

### Example

```bash
./fedora_iso_script.sh 41 /dev/sdX x86_64
```

This will download Fedora version 41 for `x86_64`, verify the download, and prompt you to write it to `/dev/sdX`.

## Script Steps

1. **Download Fedora ISO**: Fetches the Fedora ISO file from the official Fedora website.
2. **Download Checksum File**: Downloads the corresponding checksum file.
3. **Download GPG Key**: Downloads the GPG key for verification.
4. **Verify Files**:
   - **GPG Verification**: Verifies the checksum file’s signature.
   - **SHA-256 Checksum**: Validates the ISO file’s integrity using the SHA-256 checksum.
5. **Write to USB**: After successful verification, prompts to write the ISO to the specified USB device.
6. **Clean Up**: Removes the downloaded files and ejects the USB.

## Warnings and Notes

- **USB Device Caution**: Writing an ISO to the wrong device can overwrite important data. Double-check the USB device path before proceeding.
- **Root Privileges**: Writing to USB requires `sudo` privileges.

## Exit Codes

- `0`: Completed successfully or exited by the user.
- `1`: An error occurred during download, verification, or writing.

## License

MIT License
