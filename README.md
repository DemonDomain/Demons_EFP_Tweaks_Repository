# Demons S.T.AL.K.E.R Anomaly Repository
------------------------------------------------------------------------------------------------------------------------------
A list of my tweaks and documentation on how to do them yourself.
Stuff is in no particular order in this readme.
Most of the edited files relevant to this repository and the following documentation are available for download

(As i am a verified noob with Github, you sadly have to download/copy them one by one)

------------------------------------------------------------------------------------------------------------------------------
## A USEFUL NVG TWEAK

### Reduce NVG blur and noise
In `gamedata/shaders/r3/nightvision_gen_1/2/3.ps`, the following line affects the blurriness in the view.

`image = lerp(image,half_res_blur,clamp(1-smoothstep(0,15,depth),0.2,1)); // NEAR BLUR`

By changing the 0.2,1 to 0.2,0.5 for example, you reduce the amount of blur. You need to do this in all 3 files if you want the change to affect all nvg's


The following line affects the amount of noise present in the nvg view

`// APPLY NOISE
            float lua_param_nvg_gain_current = floor(shader_param_8.y) / 10.0f;
            image.r += jitter.y * (gen_3_nvg_noise_factor * (pow(lua_param_nvg_gain_current,0.5) )); // Add the noise to the image`

You can change the 0.5 to 0.25 for example to reduce the noise

------------------------------------------------------------------------------------------------------------------------------
## Gameplay related tweaks

### ReDone_Collection_2.3.4_SOUTH_MAPS_COLLECTION
If you play with Re:Done maps (south in this case), go to `gamedata\configs\scripts\escape` and open:

- `esc_smart_terrain_5_2_squad_logic.ltx`
  and
- `esc_smart_terrain_6_8_squad_logic.ltx`

Find and remove the following lines:
 
- `on_death = death@soldier`  **Remove every instance of this.**

`[death@soldier] 
on_info = {=killed_by_actor =actor_community(actor_stalker)} %=dec_faction_goodwill_to_actor(stalker:25) =send_tip(st_honor_sidorovich_deal:stalker)%`

Now you can blast the military mfers on the railway bridge and checkpoint to Garbage without repercussions.

Especially useful if you chose to start in Cordon/Rookie Village as a Loner.

------------------------------------------------------------------------------------------------------------------------------
### Difficulty tweaks (not really good to fiddle with these, but this is how to edit them anyways)

To tweak difficulties, go to `gamedata\configs\plugins\difficulty.ltx`

The file has a great explanations regarding the contents and should be pretty easy to understand.

It's advisable to have the game open on a second screen to see the min and max values, so you dont set too high or too low values depending on the setting.

Changes in `gamedata\configs\presets\economy_diff` and `gameplay_diff.ltx` dont seem to have any effect based on my experience. Most likely "leftovers" from the CoP files the game is built on

------------------------------------------------------------------------------------------------------------------------------
### New Game Loadouts

To tweak loadouts, go to `gamedata\configs\items\settings\new_game_loadouts.ltx`

If you want to add items to the pool, open game in debug mode and hold cursor on top the item you want to add

You might need to remove stuff from the pool as the game seems to have somekind of hardcoded limit on the items shown on the screen

The file itself has good guide on the top, so figuring it out is easy

------------------------------------------------------------------------------------------------------------------------------                                                              
### UI 

To change the quest arrow color from red to anything else, go to `gamedata\textures\ui`

Find `ui_hud.dds` and make a backup of the file, then open the original with your chosen photoeditor

The arrow is around the center, on the top half of the image, paint it to your desired color and overwrite the original without changes to formats etc.

---------------------------------------------------------------
If you have EFP and want to hide the sight and noise bars, find and open:

- `\mods\[Strogglet15] SquareDOV 2\gamedata\configs\ui\textures_descr\ui_SquareDOV.xml`

Change `width="256" height="256"` to `width="0" height="0"` in  lines 3 and 7



## License
This project is licensed under the Creative Commons Zero (CC0) license. You are free to use, modify, and distribute the files without any restrictions.
