# 🐳 Drosera Docker Logs Cleaner

Automatically cleans up Docker container logs every 2 hours to prevent disk space issues.

--------------------------------------------
Open your terminal and run:

    bash <(curl -s https://raw.githubusercontent.com/The-Ghost-Area/Drosera-logs-cleaner/main/auto-clean-2h.sh)

 🔍 Verify After Running
---------------------------------------------------
✅ Step 2: Check Timer Status

    systemctl status clean-docker-logs.timer


✅ Step 3: Check Last Run Status of the Service

    systemctl status drosera-logs-cleaner.service
    
✅ Step 4: Confirm the Timer is Scheduled

    systemctl list-timers | grep drosera
    
✅ Step 5: (Optional) Run the Cleanup Script Manually

    sudo systemctl start drosera-logs-cleaner.service
    
✅ Step 6: (Optional) Ensure Auto-Start on Boot

    sudo systemctl enable --now drosera-logs-cleaner.timer
