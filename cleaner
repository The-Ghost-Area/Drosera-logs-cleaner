# Step 1: Create the cleanup script
sudo tee /usr/local/bin/clean-docker-logs.sh > /dev/null << 'EOF'
#!/bin/bash

echo "[$(date)] Cleaning up Docker container logs..."

# Truncate all Docker container logs
find /var/lib/docker/containers/ -type f -name "*-json.log" -exec truncate -s 0 {} \;

echo "[$(date)] Done. Docker logs have been cleared."
EOF

# Step 2: Make the script executable
sudo chmod +x /usr/local/bin/clean-docker-logs.sh

# Step 3: Create the systemd service file
sudo tee /etc/systemd/system/clean-docker-logs.service > /dev/null << 'EOF'
[Unit]
Description=Clean Docker Container Logs
Wants=docker.service
After=docker.service

[Service]
Type=oneshot
ExecStart=/usr/local/bin/clean-docker-logs.sh
EOF

# Step 4: Create the systemd timer file (runs every 2 hours)
sudo tee /etc/systemd/system/clean-docker-logs.timer > /dev/null << 'EOF'
[Unit]
Description=Run Docker Log Cleanup Every 2 Hours

[Timer]
OnBootSec=5min
OnUnitActiveSec=2h
Persistent=true

[Install]
WantedBy=timers.target
EOF

# Step 5: Reload systemd, enable and start the timer
sudo systemctl daemon-reload
sudo systemctl enable --now clean-docker-logs.timer

# Step 6: Show timer status and next run
systemctl status clean-docker-logs.timer
echo -e "\nNext Scheduled Cleanup:"
systemctl list-timers | grep clean-docker-logs
