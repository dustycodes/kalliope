## Test your env

### Check your microphone and speaker config

To ensure that you can record your voice, run the following command to capture audio input from your microphone:
```bash
rec test.wav
```

Press CTRL-C after capturing a sample of your voice.

Then play the recorded audio file
```bash
mplayer test.wav
```

Your installation is now complete, let's take a look now to the [quickstart documentation](installation/quickstart.md) to learn how to use Kalliope.

### (Optional) Start Kalliope automatically after a reboot

If you want to start Kalliope automatically Place the script bellow in `/etc/systemd/system/kalliope.service`.
Update the path to your folder where you've placed your `brain.yml` and `settings.yml`.
```bash
[Unit]
Description=Kalliope

[Service]
WorkingDirectory=/path/to/kalliope_brain_folder

Environment='STDOUT=/var/log/kalliope.log'
Environment='STDERR=/var/log/kalliope.err.log'
ExecStart=/bin/bash -c "/usr/local/bin/kalliope start > ${STDOUT} 2> ${STDERR}"
User=%i

[Install]
WantedBy=multi-user.target
```

Then, reload systemctl, start the service and enable it at startup
```bash
sudo systemctl daemon-reload
sudo systemctl start kalliope
sudo systemctl enable kalliope
```
