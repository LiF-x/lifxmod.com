---
layout: default
last_modified_date: 2022-12-03T21:38:21.000+00:00
title: How can I configure my Life Is Feudal server to fast action
nav_order: 5
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false
published: false

---
### How can I configure my Life Is Feudal server to fast action?

Find a skill you wish to speed up

For the purposes of this tutorial, we will look at speeding up searching for Gold Deposits  
find the line with the following in your skill_types.xml

    <duration const="8 25"/>

This will be displayed as below

    			<ability lvl="60" name="Gold Deposits" type="Look for" id="5">
    				<duration const="8 25"/>
    				<ability_skill_mult>600</ability_skill_mult>
    				<entities>
    					<entity type="cell"/>
    					<entity type="tun_side"/>
    				</entities>
    				<requirements/>
    				<results>
    					<animation>perform</animation>
    					<sound>player_perform</sound>
    					<sstam_spent>10</sstam_spent>
    				</results>
    			</ability>

Then change the value to the appropriate skill type for 1 second action as shown below

    <duration const="">1</duration>

This will remove the calculation-based speed which was intended by BitBox  
\- Please take note of the removal of "8 25" to allow it to be ignored it must be deleted

> **What is the meaning of these numbers?**
>
> The 8 Resembles the maximum time it would take to complete the action
>
> The 25 resembles a Deminer, This is a division added as your skills raise which in effect reduces the minimum time taken to complete the action.  
>   
> More indepth Calculation would be as below  
> Duration = (Value1 - RealSkillLevel/Value2) * tool quality

If Correctly done this will now look like the example Below

    			<ability lvl="60" name="Gold Deposits" type="Look for" id="5">
    				<duration const="">1</duration>
    				<ability_skill_mult>600</ability_skill_mult>
    				<entities>
    					<entity type="cell"/>
    					<entity type="tun_side"/>
    				</entities>
    				<requirements/>
    				<results>
    					<animation>perform</animation>
    					<sound>player_perform</sound>
    					<sstam_spent>10</sstam_spent>
    				</results>
    			</ability>	

This is now Correctly Edited, and the same method can be used for all skill types to speed up the skills.

Skill speed is determined by the server and not the client therefore only the servers skilltypes.xml needs editing which is located in the Servers data folder