# 🐳 Drosera Docker Logs Cleaner

Automatically cleans up Docker container logs every 2 hours to prevent disk space issues.

--------------------------------------------
Open your terminal and run:

    bash <(curl -s https://raw.githubusercontent.com/The-Ghost-Area/Drosera-logs-cleaner/main/auto-clean-2h.sh)

 🔍 Verify After Running
---------------------------------------------------
✅ 1. Check if Timer is Active and Scheduled Properly

    systemctl status clean-docker-logs.timer
    

✅ 2. See When the Timer is Next Scheduled

    systemctl list-timers | grep clean-docker-logs
    
    
✅ 3. Check Last Run Result of the Service

    systemctl status clean-docker-logs.service


✅ 4. View Logs of the Cleanup Script

    journalctl -u clean-docker-logs.service --since "2 hours ago"

    
✅ 5. Test the Script Manually (Optional)

    sudo systemctl start clean-docker-logs.service

    


