---
layout: default
last_modified_date: 2022-12-03T15:38:46.000+00:00
title: Enable Personal Claims on a Red World
nav_order: 1
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false

---
### Enable Personal Claims on a Red World

In order to activate Personal Claims on a Red World you will need to edit both the Server’s and Client’s **skill_types.xml** files. Below you can find examples of how we recommend you should edit your file.

The Abilities you will need to edit from

    <req type="world">green</req>

to

    <req type="world">red</req>

are:  
Worship

* Private Land
* Resize
* Remove!
* Undo Claim Resize

  Information Below is for the changes
* Worship

      <ability lvl="0" name="Worship" type="Special" id="355">
          <duration const="">1</duration>
          <ability_skill_mult>0</ability_skill_mult>
          <entities>
              <entity type="complex_obj">
                  <ent_reqs>
                      <ent_req type="object_type_id">1444</ent_req>
                      <ent_req type="state">incomplete complete damaged</ent_req>
                      <ent_req type="claim" usage_type="use"/>
                  </ent_reqs>
              </entity>
          </entities>
          <requirements>
              <req type="world">red</req> <!-- Default: green -->
              <req type="onhorse">allowed</req>
              <req type="oncart">denied</req>
          </requirements>
          <results>
              <animation>pray</animation>
              <sound>player_perform</sound>
              <sstam_spent>10</sstam_spent>
          </results>
      </ability>
* Private Land

                  <ability lvl="0" name="Private Land" type="Claim" id="290">
                      <duration const="">5</duration>
                      <ability_skill_mult>0</ability_skill_mult>
                      <entities>
                          <entity type="cell">
                              <ent_reqs>
                                  <ent_req type="claim" usage_type="claim"/>
                              </ent_reqs>
                          </entity>
                          <entity type="complex_obj">
                              <ent_reqs>
                                  <ent_req type="state">incomplete</ent_req>
                                  <ent_req type="object_type_id">1444</ent_req>
                              </ent_reqs>
                          </entity>
                      </entities>
                      <requirements>
                          <req type="world">red</req> <!-- Default: green -->
                      </requirements>
                      <results>
                          <animation>pray</animation>
                          <sound sid="91"/>
                          <sstam_spent>50</sstam_spent>
                      </results>
                  </ability>
* Resize

      <ability lvl="0" name="Resize" type="Claim" id="291">
          <duration const="">5</duration>
          <ability_skill_mult>0</ability_skill_mult>
          <entities>
              <entity type="cell">
                  <ent_reqs>
                      <ent_req type="distance">0</ent_req>
                      <ent_req type="claim" usage_type="claim"/>
                  </ent_reqs>
              </entity>
          </entities>
          <requirements>
              <req type="world">red</req> <!-- Default: green -->
          </requirements>
          <results>
              <animation>pray</animation>
              <sound sid="91"/>
              <sstam_spent>10</sstam_spent>
          </results>
      </ability>
* Remove!

      <ability lvl="0" name="Remove!" type="Claim" id="292">
          <duration const="">5</duration>
          <ability_skill_mult>0</ability_skill_mult>
          <entities>
              <entity type="cell">
                  <ent_reqs>
                      <ent_req type="claim" usage_type="claim"/>
                  </ent_reqs>
              </entity>
          </entities>
          <requirements>
              <req type="world">red</req> <!-- Default: green -->
          </requirements>
          <results>
              <animation>pray</animation>
              <sound sid="91"/>
              <sstam_spent>10</sstam_spent>
          </results>
      </ability>
* Undo Claim Resize

      <ability lvl="0" name="Undo Claim Resize" id="329">
          <duration const="">5</duration>
          <ability_skill_mult>0</ability_skill_mult>
          <entities>
              <entity type="cell">
                  <ent_reqs>
                      <ent_req type="claim" usage_type="claim"/>
                  </ent_reqs>
              </entity>
          </entities>
          <requirements>
              <req type="world">red</req> <!-- Default: green -->
          </requirements>
          <results>
              <animation>pray</animation>
              <sound sid="91"/>
              <sstam_spent>10</sstam_spent>
          </results>
      </ability>