Postmortems: are a process intended to help us learn from past incidents. They typically involve a blame-free analysis and discussion soon after an issue has taken place. The purpose is to produce an artifact that includes a detailed description of exactly what went wrong to cause the issue/incident, along with a list of steps to prevent similar incidents in the future. An analysis of how the organization’s incident response process worked during the event is also usually included.


Organizations may refer to this process in slightly different ways, such as a “Learning Review”, “After-Action Review”, “Incident Review”, “Incident Report”, “Post-Incident Review”, or “Root Cause Analysis (RCA)”.

Issue Summary
On April 3rd, 2024 at 11:00 AM GMT , our primary database server experienced a critical failure, resulting in a complete outage of our e-commerce platform. The outage lasted for 3 hours and 14 minutes, until 2:16 PM GMT. During this time, 100% of our customers were unable to access the website, view products, or place orders. This incident resulted in a lot of lost.

The root cause

was a hardware failure that led to data corruption in the primary database, causing the entire system to become unresponsive.

Timeline:
11:02 AM GMT— Website becomes unresponsive, returning 503 errors.
11:05 AM GMT— Monitoring system triggers an alert, notifying the on-call engineering team.
11:10 AM GMT— Initial investigation determines the database server is the source of the issue.
11:15 AM GMT— Team attempts to restart the database service, but the server remains unresponsive.
11:30 AM GMT— Database backups are checked, and it’s discovered that the latest backup is also corrupted.
12:00 PM GMT— The incident is escalated to the senior engineering and leadership teams.
12:30 PM GMT— Decision made to failover to the secondary database server, which is also found to be corrupted.
1:00 PM GMT— Team begins restoring the database from the previous day’s backup, a time-consuming process.
2:00 PM GMT— Restored database is brought online, and the website gradually returns to normal operation.
2:16 PM GMT— Website fully restored and operating normally.

Root Cause and Resolution:
The root cause of the outage was a hardware failure on the primary database server, which led to corruption of the database files. The failure was caused by a faulty hard drive that experienced a catastrophic failure, rendering the data stored on it unusable.

The issue was resolved by restoring the database from the previous day’s backup, which was the only viable option due to the corruption of the latest backup. This process took over an hour to complete, as the previous day’s backup needed to be transferred to the secondary server and then brought online.

Corrective and Preventative Measures:

Implement a comprehensive database backup and recovery strategy, including regular testing of the restoration process.
Upgrade the database hardware to use enterprise-grade, redundant storage solutions to prevent single points of failure.
Investigate the use of a high-availability database cluster to provide automatic failover and minimize downtime in the event of a hardware failure.
Enhance the monitoring and alerting system to provide earlier detection of issues, with clear escalation paths to the appropriate teams.
Conduct regular disaster recovery drills to ensure the team is prepared to respond effectively to similar incidents in the future.
Review and update the incident response plan to include more detailed steps for database restoration and recovery.
