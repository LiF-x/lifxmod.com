---
layout: default
last_modified_date: 2023-01-11 11:48:11 +0000
title: How to activate enslavement during non jh
nav_order: 10
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false

---
Open your Skill_types.xml

Find the Enslave block and Remove the Requirements

    			<ability lvl="0" name="Enslave" id="345">
    				<duration const="">6</duration>
    				<ability_skill_mult>0</ability_skill_mult>
    				<icon>art\2D\skills\abilities\coup_de_grace.png</icon>
    				<entities>
    					<entity type="player">
    						<ent_reqs/>
    					</entity>
    				</entities>
    				<requirements>
    					<req type="warstance">allowed</req>
    					<req type="world">red</req>
    					<req type="jh">only</req>
    				</requirements>
    				<results>
    					<animation>mowing</animation>
    					<sound>player_perform</sound>
    					<sstam_spent>30</sstam_spent>
    				</results>
    			</ability>
    		</abilities>
    	</row>

so it looks like the below block, ensure this file is shared with client.

    <ability lvl="0" name="Enslave" id="345">
    				<duration const="">20</duration>
    				<ability_skill_mult>0</ability_skill_mult>
    				<icon>art\2D\skills\abilities\coup_de_grace.png</icon>
    				<entities>
    					<entity type="player">
    						<ent_reqs/>
    					</entity>
    				</entities>
    				<results>
    					<animation>mowing</animation>
    					<sound>player_perform</sound>
    					<sstam_spent>30</sstam_spent>
    				</results>
    			</ability>
    		</abilities>
    	</row>

 