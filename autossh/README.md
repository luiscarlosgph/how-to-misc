Autossh in Mac OS X
-------------------

1. Install autossh:
   ```bash
   $ brew install autossh
   ```

2. Change `SSHConnectionHere` by the name of your SSH connection (i.e. the name you use in your `.ssh/config`) and `UsernameHere` and save this file to `/Library/LaunchDaemons/local.autossh.plist`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
        <key>Label</key>
        <string>local.autossh</string>
        <key>KeepAlive</key>
        <true/>
        <key>ProgramArguments</key>
        <array>
        <string>/opt/homebrew/bin/autossh</string>
                <!-- autossh switches -->
                <string>-M</string>
                <string>0</string>

                <!-- ssh switches -->
                <string>-N</string>

                <string>-o</string>
                <string>ControlMaster no</string>

                <string>-o</string>
                <string>ServerAliveInterval 60</string>

                <string>-o</string>
                <string>ServerAliveCountMax 3</string>

                <string>SSHConnectionHere</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>UserName</key>
        <string>UsernameHere</string>
        <key>StandardErrorPath</key>
        <string>/dev/null</string>
        <key>StandardOutPath</key>
        <string>/dev/null</string>
   </dict>
   </plist>
   ```