# Cross-Region-Backup-Replication-for-EC2-using-AWS-Backup
Internship Project -1

🎯 Objective

The objective of this project is to configure AWS Backup to automatically back up an EC2 instance and replicate the backup to another AWS Region.

Cross-region backup replication provides an additional copy of the backup in a geographically separate region. This improves data durability and disaster recovery readiness.

🏗️ Project Architecture :
<img width="800" height="559" alt="image" src="https://github.com/user-attachments/assets/632b5f36-2900-42dc-b964-14e48ac497fe" />



🎯  AWS Regions Used


| Purpose                 | Region                       |
| ----------------------- | ---------------------------- |
| Source / Primary Region | Mumbai (`ap-south-1`)        |
| Destination / DR Region | Singapore (`ap-southeast-1`) |


🎯1. EC2 Instance Setup

 <img width="1366" height="768" alt="Screenshot (114)" src="https://github.com/user-attachments/assets/2033f6a2-53c4-4aaa-8439-47246428b3f1" />


<img width="1366" height="768" alt="Screenshot (115)" src="https://github.com/user-attachments/assets/bc0f192d-4cce-4b93-89dd-2d797d77167d" />


🎯 2. Create Source Backup Vault 


A Backup Vault is a secure storage location in AWS Backup where backup recovery points are stored.

Steps to Create a Backup Vault
1 Open the AWS Management Console.
2 Go to AWS Backup.
3 Select Backup vaults from the left-side menu.
4 Click Create backup vault.
5 Enter a vault name, for example:
6 EC2-Backup-Vault
7 Select the required Encryption key.
8 Optionally enable Vault Lock for additional protection.
9 Click Create backup vault.


🎯 Purpose

The Backup Vault is used to:

Store EC2 backup recovery points.
Protect backups from accidental deletion.
Control backup retention.
Provide a secure location for backups.
Store backup copies used for disaster recovery.

🎯 3 Create Source Backup Vault

The first backup vault was created in the Mumbai region.
<img width="1366" height="768" alt="Screenshot (116)" src="https://github.com/user-attachments/assets/6664dc5f-8d27-463c-aff1-9d82033548b0" />

<img width="1366" height="768" alt="Screenshot (117)" src="https://github.com/user-attachments/assets/7964d24c-a5be-4f9b-a5a5-34161cb86ef1" />



🎯 Create Destination Backup Vault

A second backup vault was created in the Singapore region.


🎯4 Create AWS Backup Plan

A backup plan was created in the Mumbai region.
 Create AWS Backup Plan

An AWS Backup Plan defines when backups should be created, how often they should run, where they should be stored, and how long they should be retained.

Steps to Create an AWS Backup Plan
Open the AWS Management Console.
Go to AWS Backup.
Select Backup plans from the left-side menu.
Click Create backup plan.
Select Build a new plan.

Enter the backup plan name:

EC2-CrossRegion-Backup-Plan

Under Backup rule, enter the rule name:

DailyEC2Backup

Select the Backup vault created earlier:

EC2-Backup-Vault

Set the Backup frequency to Daily.
Configure the required backup window.
Configure the retention period, for example:

30 days

If required, configure Copy to destination for cross-region backup replication.
Review the settings.
Click Create plan.
<img width="1366" height="768" alt="Screenshot (122)" src="https://github.com/user-attachments/assets/50884fca-b4be-4a9f-9b63-e2842426dfcb" />

##Create Backup Rule<img width="1366" height="768" alt="Screenshot (123)" src="https://github.com/user-attachments/assets/45ccb76c-6aac-4be1-a7e6-e28b2bec0bed" />
##12. Cross-Region Copy Validation
14. Validation Checklist
 EC2 instance launched successfully.
 Sample files created on the EC2 instance.
 Source backup vault created.
 Destination backup vault created.
 Backup plan created.
 Daily backup rule configured.
 EC2 instance assigned to the backup plan.
 Cross-region copy configured.
 On-demand backup triggered.
 Local backup job completed successfully.
 Cross-region copy job completed successfully.
 Destination recovery point verified.

 16. Benefits of Cross-Region Backup
1. Disaster Recovery

If the primary AWS Region experiences a major failure, the backup is available in another region.

2. Data Protection

An additional copy of the backup provides better protection for important data.

3. Geographic Separation

The backup is stored in a geographically separate AWS Region.

4. Automated Backup

AWS Backup automatically performs backups according to the configured backup plan.

5. Business Continuity

Cross-region backups help organizations recover their workloads after a regional failure.

Conclusion

This project demonstrates how AWS Backup can be used to protect an EC2 instance and replicate its backups across AWS Regions. A backup plan was created with a scheduled backup rule, the EC2 instance was assigned to the plan, and cross-region copy was configured from Mumbai to Singapore.

An on-demand backup was triggered for immediate validation. The backup job and cross-region copy job were checked for successful completion, and the replicated recovery point was verified in the destination backup vault.

This setup provides a foundation for disaster recovery, data protection, and business continuity by maintaining a backup copy outside the primary AWS Region.
