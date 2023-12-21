# PostgreSQL Backup Script Readme

This shell script is designed to facilitate the backup of a PostgreSQL database. It allows users to easily configure and schedule daily backups, providing flexibility and control over the backup process. The script utilizes a configuration file to set various parameters, making it adaptable to different PostgreSQL setups.

## Prerequisites

- **PostgreSQL**: Ensure that PostgreSQL is installed on your system and the necessary tools like `pg_dump` are available.

## Configuration

1. **Create Config File**: Create a configuration file named `backup_config.sh`. Use the following template and adjust the values based on your requirements.

   ```bash
   # backup_config.sh

   # Directory to store backups
   BACKUP_DIR="/postgres/pgsql/13/BACKUP/"

   # PostgreSQL username
   USERNAME="postgres"

   # Number of days to keep daily backups
   DAYS_TO_KEEP_DAILY_BACKUPS=7

   # Number of weeks to keep weekly backups
   WEEKS_TO_KEEP_WEEKLY_BACKUPS=4

   # Enable plain backups (yes/no)
   ENABLE_PLAIN_BACKUPS="yes"
   ```

   Adjust the values of `BACKUP_DIR`, `USERNAME`, `DAYS_TO_KEEP_DAILY_BACKUPS`, `WEEKS_TO_KEEP_WEEKLY_BACKUPS`, and `ENABLE_PLAIN_BACKUPS` according to your preferences.

## Running the Script

1. **Make Script Executable**: Ensure that the script is executable by running the following command:

   ```bash
   chmod +x postgres_backup.sh
   ```

2. **Execute the Script**: Run the script by executing the following command:

   ```bash
   ./postgres_backup.sh
   ```

   The script will read the configuration from the `postgres_backup.config` file and initiate the backup process.

## Scheduling Daily Backups

To schedule daily backups, you can use tools like `cron` on Unix-based systems. Here's an example of scheduling the script to run every day at 2:00 AM:

1. Open the crontab file for editing:

   ```bash
   crontab -e
   ```

2. Add the following line to schedule the script:

   ```bash
   0 2 * * * /path/to/postgres_backup.sh
   ```

   This example runs the script every day at 2:00 AM. Adjust the timing according to your preferred schedule.

Now, your PostgreSQL database will be backed up daily based on the configuration provided in the `backup_config.sh` file. Adjust the settings as needed to meet your specific backup requirements.
