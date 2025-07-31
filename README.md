# Demons S.T.AL.K.E.R Anomaly Repository &#x1F4DD;
------------------------------------------------------------------------------------------------------------------------------
A list of tweaks and other useful knowledge regarding file edits, i just add shit whenever i come across useful info.
Stuff is listed as i come across info, so newest stuff is towards the bottom.
Most of the edited files relevant to this repository are uploaded for storage/backup purposes

------------------------------------------------------------------------------------------------------------------------------
## &#x2699; NVG BLUR AND NOISE
In `gamedata/shaders/r3/nightvision_gen_1/2/3.ps`, the following line affects the blurriness.
By default its 0.2,1. You need to do this in all 3 files if you want the change to affect all nvg's

`image = lerp(image,half_res_blur,clamp(1-smoothstep(0,15,depth),0.2,0.5)); // NEAR BLUR`

The following line affects the amount of noise present in the nvg view
You can change the 0.5 to 0.25 for example to reduce the noise

`// APPLY NOISE
            float lua_param_nvg_gain_current = floor(shader_param_8.y) / 10.0f;
            image.r += jitter.y * (gen_3_nvg_noise_factor * (pow(lua_param_nvg_gain_current,0.5) )); // Add the noise to the image`
            
------------------------------------------------------------------------------------------------------------------------------
## &#x1F527; Gameplay related
If you play with Re:Done maps (south in this case), go to `gamedata\configs\scripts\escape` and open:

- `esc_smart_terrain_5_2_squad_logic`
- `esc_smart_terrain_6_8_squad_logic`

Find and remove the following lines:
 
- `on_death = death@soldier`  **Remove every instance of this.**

`[death@soldier] 
on_info = {=killed_by_actor =actor_community(actor_stalker)} %=dec_faction_goodwill_to_actor(stalker:25) =send_tip(st_honor_sidorovich_deal:stalker)%`

Now you can blast the military mfers on the railway bridge and checkpoint to Garbage without repercussions.
Especially if you chose to start in Cordon/Rookie Village, especially as a Loner.
------------------------------------------------------------------------------------------------------------------------------
## &#x2757; Difficulty tweaks

To tweak difficulties, go to `gamedata\configs\plugins\difficulty.ltx`
It's advisable to have the game open on a second screen for reference(to see the minimums/maximums etc)
Changes in `gamedata\configs\presets\economy_diff` and `gameplay_diff.ltx` dont seem to have any effect.

------------------------------------------------------------------------------------------------------------------------------
## &#x1F4C4; New Game Loadouts

To tweak loadouts, go to `gamedata\configs\items\settings\new_game_loadouts.ltx`
If you want to add items to the pool, open game in debug mode and hold cursor on top the item you want to add
You might need to remove stuff from the pool as the game seems to have somekind of hardcoded limit on the items shown on the screen
The file itself has good guide so figuring it out is easy

------------------------------------------------------------------------------------------------------------------------------                                                              
## &#x2705; UI 

To change the questarrow color from red to anything else, open:

- `gamedata\textures\ui\ui_hud.dds`

The arrow is around the center, on the top half of the image

---------------------------------------------------------------
If you have EFP and want to hide the sight and noise bars, find and open:

- `\mods\[Strogglet15] SquareDOV 2\gamedata\configs\ui\textures_descr\ui_SquareDOV.xml`

Change `width="256" height="256"` to `width="0" height="0"` in  lines 3 and 7



## License
This project is licensed under the Creative Commons Zero (CC0) license. You are free to use, modify, and distribute the files without any restrictions.
