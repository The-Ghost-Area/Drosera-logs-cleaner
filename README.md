# 🐳 Drosera Docker Logs Cleaner

Automatically cleans up Docker container logs every 2 hours to prevent disk space issues.

--------------------------------------------
Open your terminal and run:

    bash <(curl -s https://raw.githubusercontent.com/The-Ghost-Area/Drosera-logs-cleaner/main/auto-clean-2h.sh)

 🔍 Verify After Running
---------------------------------------------------
Timer status check:

    systemctl status clean-docker-logs.timer

Next scheduled cleanup dekhne ke liye:

    systemctl list-timers | grep clean-docker-logs
    
Manual test karne ke liye:

    sudo systemctl start clean-docker-logs.service
