## Linux Practice note

### Process checks
**How a process run?**
A process runs in two ways:
- Foreground: A process runs by default in foreground and requires a keyboard input. it blocks the terminal for other commands.
  eg. Sleep 10 (No other command can be run in the terminal until it finishes)
  fg command is use to check the foreground process.
- Background: Do not require a keyboard input while running. To run a process in background add an & at the end of the command.
  It makes the terminal free for other commands.
  eg. Sleep 60 &
  output: [1] 2456 where
          1 is job number
          2456 is process id
- ps: shows the list of all the active running processes.
- ps aux: detailed list of all the running processes.
  a - all users
  u - show user/owners
  x - processes not executed
- Kill: A process will get hung you will need to kill it.
  eg. kill -9 <pid>, -9 is for force kill
- htop or top: live process monitoring

### Service checks
- systemctl status <service-name>: tells whether a service is acttive or not. Shows process id.
- systemctl list-units --type=service --state=running: lists all the running services.
- sudo systemctl start/stop/restart <service-name>

### Log check Commands
- journalctl -u <service-name>: gives the logs of a particular service
- journalctl -u <service-name> --no-pager | tail -n 20: gives latest logs
- journalctl -u <service-name> -f: live logs
- tail -n 50 /var/log/syslog: gives system level logs

### mini troubleshooting flow
Issue: **SSH can't login**

1. Check service
   - systemctl status ssh
2. check process
   - ps aux | grep ssh
3. Check Port
   - ss -tuln | grep 22
4. Check logs
   - journalctl -u ssh | tail


## day -04 done




          
