*Back to [Introduction page](https://github.com/teusink/Home-Security-by-Pi/blob/master/README.md)*

# Maintenance
Ultimally, the core practice of Security is just to install all (security) updates. This is not different from your Pi. Below I will explain how I did that.

## Raspberry Pi & Pi-hole
Your Pi and all software installed through `apt-get` can be updated with a single script, and you can incorporate additional commands to update additional sources.

- Create a script called `pi-update.sh` and place it in the Pi's home folder. You can find the contents of the script here: https://github.com/teusink/Secure-my-Pi/blob/master/pi-update.sh
- Edit your crontab to plan a regular execution of the script using `crontab -e`.
- Add this line: `0 5 * * SUN sudo sh /home/pi/pi-update.sh >/home/pi/pi-update.log`. This line means that it will do an update every Sunday at 5 am and it outputs it logs to a log file.
- Add this line: `0 6 * * SUN sudo /usr/sbin/ssmtp your_account_name@domain.tld < /home/pi/pi-update.log `. This line means that the log-file created in the update above will be emailed to you every Sunday at 6 am.

## OpenVPN
OpenVPN has unattended upgrades and it upgrades itself. No further configuration required here.

# Done
- This part is done now, so do a reboot now: `sudo reboot`