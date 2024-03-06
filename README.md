# AWS Cloud Cost Optimization - Identifying Stale Resources

## Identifying Stale EBS Snapshots

Create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

### Description:

The Lambda function fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.

## Project step by step
### Part 1 
- Create EC2 instance
- Create Snapshots

### Part 2
- Create lamda function
- Edit timout for 10 seconds (Default 3s)
- Create policy in IAM include (DeleteSnaphots, DescribeSnapshots, DescribeInstances, DescribeVolumes) for all resources
(Snapshots will be delete if it not associate with volume(exists if EC2 run) )

### Part 3
- Set CloudWatch 
- Set in rule in schedule for 1 time everyday

