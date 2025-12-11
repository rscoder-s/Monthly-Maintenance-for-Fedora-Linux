***

# Monthly Maintenance for Fedora

A lightweight system utility for Fedora Workstation that manages monthly feature and kernel updates. It provides a native Libadwaita GUI installer and a "nag-style" notification system to ensure you never miss your designated maintenance window.

### Philosophy: The "Stable Rolling" Model
This tool is designed to be used in conjunction with `dnf-automatic` to emulate the release cadence of major operating systems (like Windows or macOS):
1.  **Security:** Your system applies critical security patches daily in the background (via `dnf-automatic`).
2.  **Features:** This tool prompts you on the 1st of every month to apply kernel, driver, and application feature updates.

This hybrid approach gives you enterprise-grade security responsiveness with the stability of a monthly update cycle.

### Prerequisites
To achieve the intended workflow, you must configure Fedora to auto-install security patches:
1.  Install `dnf-automatic`.
2.  Edit `/etc/dnf/automatic.conf`: set `upgrade_type = security` and `apply_updates = yes`.
3.  Enable the timer: `sudo systemctl enable --now dnf-automatic.timer`.

### Dependencies
* `python3-gobject`
* `python3-libadwaita`
* `libnotify`
* *(Optional)* `distrobox` (if you use containers)

### Installation
1.  Download the latest release and extract the zip file.
2.  Double-click the **`Install`** file.
3.  Click **Install**.

*The installer automatically configures the executable, desktop shortcut, and autostart entry.*

### Usage
* **Automatic:** On the 1st of every month, a notification will appear if you haven't updated yet. Click it to review and apply updates via the GUI.
* **Manual:** Launch **Monthly Maintenance** from your App Grid anytime to check system status or view logs.
* **Verification:** Check `~/.config/monthly-updater/maintenance.log` for a full audit trail.

### Uninstall
Run the **`Install`** file again and click **Uninstall**. This removes the binary, configuration, logs, and autostart entries cleanly. If the tool isnt running right and you'd like to reinstall and reconfigure everything, you can also **Repair** your installation of Monthly Maintenance.
