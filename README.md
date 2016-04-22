Schedule cron job
Schedule cron job to take back up of database. Ste…
SCHEDULE CRON JOB TO TAKE BACK UP OF DATABASE.
Step 1: Go to schedule cron job option on your server.
E.g. In textdrive go system>scheduled cron job

Step 2: Create on shell file to run command to take backup of database.

e. g. daily_backup.sh

Paste this commands in daily_backup.sh file.

#!/bin/sh
# This file will run a backup of your desired MySQL database and

# remove any backups older than 7 days.

#

# If you’d like to preserve backups for longer than a week, like say

# 2 weeks, then set the ‘-mtime’ value from ‘+7′ to ‘+14′.

#

# NOTE: Make sure to create a ‘backups’ folder in the root of your

# account and replace username, password, and database_name with

# the appropriate values.

/usr/local/bin/mysqldump –opt –skip-add-locks database_name –user=username –password=password > /users/home/username/backups/file_name_`date “+%Y-%m-%d”`.sql

cd /users/home/username/backups/

/usr/bin/find *.sql -mtime +7 –delete

Keep this file in /users/home/username/script/
Step 3: Select create a new scheduled cron job option.

Write in command field

/bin/sh /users/home/username/script/daily_backup.sh

Step 4: you can select option for when to execute select simple schedule and select daily option from drop down list.

Step 5: Save cron job.
