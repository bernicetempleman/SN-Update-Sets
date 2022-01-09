# SNOW-Update-Sets

- An update set is a group of customizations that can be moved from one instance to another. 

- Update sets allow administrators to group a series of changes into a named set and then move them as a unit to other systems. 
- In most cases, Update Sets allow customizations to be developed in a development instance, moved to a test instance, and then applied to a production instance. 

- For example, a set of enhancements to incident management can be grouped in an update set called Incident Management 2.0.
-  While Incident Management 2.0 is marked as the current update set, all changes are tracked in it.

- Update Set Table: sys_update_set

- Before using update sets, we should know how to plan the update process and avoid common pitfalls.
-  Then, create an update set and use it to make changes on a development instance.
-   You can report on updates, merge update sets, and compare update sets to ensure the desired changes are ready to move.

## An update set consists of:

- A set of record details that uniquely identify the update set.
- A list of configuration changes.
- A state that determines whether another instance can retrieve and apply configuration changes.

- By default, update sets only track changes to baseline applications and platform features.
-  This allows developers to create functionality on a sub-production instance and promote the changes to another instance.

## Administrators have the following options with update sets.

 - Create an update set to store local changes.
 - Select the current update set to store local changes.
 - Compare update sets to determine what differences they contain.
 - Merge separate update sets into a single update set.
 - Retrieve update sets from remote instances.
 - Apply retrieved update sets.
 - Back out changes applied from an update set.
 - Preview & Commit an update Set

## Planning th Update Process
Before working with update sets, create a standard process for moving customizations from instance to instance. Review the following items to ensure that there are no problems during the update set process:

Check that both instances are the same version. Customizations may not work if they rely on code that has changed between versions.

2) Determine the changes to make in a single update set. ServiceNow     recommends limiting update sets to a maximum of 100 records. This maximum value helps to prevent conflicts and makes reviewing the update set easier.

3) Ensure that all base system records have matching sys_id fields. Some base system records are created on an instance after provisioning and do not match between different instances, leading to problems with update sets. The best way to avoid this issue is to:

 Provision production and sub-production instances.
 Clone the production instance onto the sub-production instance.

4) Identify a common path for update sets to move from instance to instance and maintain that model. Never migrate the same update set from multiple sources. Best practice is to move update sets from dev to test and then from test to production.

5) Plan for when to commit the update set to production. Avoid committing an update set to a production instance during business hours. The instance may perform slower temporarily as the update set applies.

6) Make sure update set names are clear. Create a naming convention to coordinate changes from multiple developers and to reference when committing the changes to another instance.
 If update sets are being generated as fixes for problems, consider including the problem ticket in the name (for example, PR10005 - Duplicate Email Issues Fix).
 If more than one update set is needed to address a problem, include a sequence number in the naming convention so that update sets are applied in the order that they were created (for example, PR10005 - Duplicate Email Issues Fix and PR10005.2 - Duplicate Email Issues Fix).

## Avoiding common pitfalls
In addition to planning the process, make sure to avoid common pitfalls: 

1) Do not delete update set. If an update set is deleted, any updated records may be overwritten in the next update.

2) Do not back out the Default update set. This action causes damage to the system.

3) Do not mark an update set as Complete until it is ready to migrate. Once an update set is complete, do not change it back to In progress. Instead, create another update set for the rest of the changes, and make sure to commit them together in the order that they were created. Naming conventions may help in this case (for example, Performance Enhancements and Performance Enhancements 2).

4) Do not manually merge updates into an update set. Always use the Merge Update Sets module. This tool compares duplicate files between update sets and selects the newest version.

 
5) If a committed update set has a problem in the test instance, build the fix in another update set in the development instance. Commit this set to the test instance, and then make sure both sets are migrated to the production instance and committed in the order they were made.

6) Always preview an update set before committing it.

7) Set completed update sets on the production instance to ignore. This state ensures the update set is not reapplied when cloning the instance.

8) Keep a to-do list of manual changes and data loads that need to be completed after an update set is applied.

9) Do not make too many changes at one time. Verify that the correct changes have been made incrementally.

## Customizations in an update set
An Update Set is an XML file that contains a list of changes to an instance. Administrators can save an Update Set as a local file that can be transferred to another instance.

Typically you create an Update Set when one of the following conditions apply:

 The two instances do not have network connectivity so you cannot retrieve Update Sets from the remote instance nor create a data source to pull, or import, data directly from the source instance
 You do not want to provide administrator credentials to the source instance (for example, you do not want to share an administrator password with people outside your company) so you cannot retrieve Update Sets nor create a data source
 You want to back up important customizations locally
![image](https://user-images.githubusercontent.com/12488769/148685941-a0428458-fe47-4a0c-aea6-47a6fd24e5e1.png)

## Practical
Creation of an Update Set
Previewing an Update Set
Execution of an Update Set
Merging Of an Update Set
Transfer from one instance to another instance











