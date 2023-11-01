# How to install
1. Just copy all the files with replacement of the files from this folder to the root folder with the installed game.

## Changelog
```
Last update: April 29, 2020.

Platform: LADC 1.4007
Author: V@leroK
Uses: OGSR, STCoP, SWM
Acknowledgements: Shoker, Mortan, rafa, KRordinn, Old Serpski Stalker
------------------------------------------------------------------------------- 
                     List of engine changes
-------------------------------------------------------------------------------
Changes:
1. High quality fix by Shoker
2. Fixed drawing of addons (when the sight was put on and the model did not appear).
3. Added streifs from Shoker Mod 
4. Added smooth camera transition when crouching
5. Added sound of switching modes of dynamic sight
6. Reduced Hud Viewport, now the weapon will not be translucent due to close proximity to the camera
7. Rain sound does not disappear when loading a save
8. Added console command to turn off sound mashing, see below.
9. Reduced RAM consumption, thanks to this there will be no more memory crashes. (Big thanks to Shoker's)

Console Commands: 
g_fix_shoot_snd (0-1) - Turns off sound mashing (there are rare bugs with sound loss, but as for me it is worth it), by default it is enabled.
r1_no_ram_textures (on, off) - Option responsible for storing textures in video memory, works only for r1 and r2 (DX9). By default it is off, but can be enabled (there are bugs with alt+tab). After enabling you need to restart the game. For r3 and r4 (DX10, DX11) the edit is enabled by default without console commands.

For developers:
1. Added support for multi-targeting and collimators from STCoP
2. Added support for multiple weapon animations (must be specified in config) see below.
3. Added scripting methods for future animation pack update, see below
4. Added but by default disabled knife wear when hitting a target, affects damage. In the next update of the knife pack the edit will be involved
5. To customize the strifes are required parameters below, specified in the hood of the weapon.
6. Added console commands, see below
7. Added a cartridge in the chamber. additional_ammo = true in the weapon config. Default is off because there are rare bugs with the duping of ammo when seiv-load.
8. At the wedge disappears 1 cartridge. misfire_anim = true in the weapon config. By default it is off.

Let me explain about memory usage. Textures will now be stored in video memory without loading RAM. 
If the video memory runs out, the textures will be loaded into RAM. 
So I recommend to include the edit for everyone, but a good result will be the owners of 4 gb of video memory, and the best from 6 gb.

Regarding point 8, added a console command that removes the mashing of the sound of gunshots, which is very positive impact on the perception of the weapon pack. 
However, unfortunately, sometimes because of the shooting of rapid-fire guns like the OC-33 sound can disappear for a couple of seconds, but then return.

Strife settings and default parameters:
	strafe_enabled = true Enable effect?
	strafe_transition_time = 0.25 Speed of the effect
	strafe_hud_offset_pos = 0.015,0.0,0.00 Shift of hud when strafe_hud_offset_pos.
	strafe_hud_offset_rot = 0.0,0.0,0.0,4.5 Rotation of the skin when streaking.

	Settings for aiming mode:
	strafe_aim_enabled = false Enable effect?
	strafe_aim_transition_time = 0.3 Effect speed
	strafe_aim_hud_offset_pos = 0.005,0.0,0.00 Shift of hood when strafe_aim_hud_offset_pos = 0.005,0.0,0.00 Shift of hood when strafing
	strafe_aim_hud_offset_rot = 0.0,0.0,0.0,0.6 Rotation of the hood when streaking.

Memo:
_g - Underbarrel Grenade Launcher
_w_gl - Weapon that supports underbarrel grenade launcher but it is not attached
_misfire - Wedge misfire
_firemode - Change fire mode
_empty_fire - Pulling the trigger when the magazine is empty
_aim - In aiming

Animations:

anim_reload_empty_w_gl
anim_reload_misfire
anim_reload_misfire_w_gl
anim_firemode
anim_firemode_w_gl
anim_empty_fire_g
anim_empty_fire_w_gl
anim_empty_fire
anim_shots_aim
anim_shots_w_gl_aim
anim_reload_misfire_empty
anim_reload_misfire_w_gl_empty
anim_firemode_empty
anim_firemode_w_gl_empty
anim_shots_misfire
anim_empty_fire_misfire
anim_firemode_misfire

Sounds for animations:

snd_firemode
snd_reload_empty
snd_reload_misfire

Scripted methods:

List of the classes exported to LUA

C++ class game_object {
	function activate_detector(boolean, boolean); - Detector activation. The first boolean - Flag of quick activation, the second - Is it necessary to get the bolt?
	function deactivate_detector(boolean); - Deactivation of the detector, boolean - Flag of quick deactivation.
	function activate_detector_anim(boolean); - Activation of the detector in the 10th slot, boolean - Flag of quick activation.
	function deactivate_detector_anim(boolean); - Deactivation of the detector in the 10th slot, boolean - Flag of quick deactivation.
	function set_nv_state(boolean, boolean); - Set the status of the NV. The first argument - activation, the second - whether to play sound. Does not work without a flashlight in the slot.
	function get_nv_state(); - Output the current status of the NV. Does not work without a flashlight in the slot.
	function actor_state(); - Issue the current status of the actor.
	function hide_weapon_anim(); - Hiding weapons, except for the 10th slot.
	function restore_weapon_anim(); - Restore weapons.
	function hide_weapon_single(); - Hiding all two-handed items.
	function restore_weapon_single(); - Restore two-handed items.
	function block_slots(boolean); - Prohibit switching to other slots, the active item remains in your hand.
	function is_blocked_slots(); - Is it forbidden to switch to other slots?
	function is_det_active(); - Is the detector active now?
	function is_det_active_anim(); - Is the detector in the 10th slot active now?
	function clear_helmet(); - Clears drops from the actor's helmet.
};

The _anim prefix and the 10th slot are methods for the animation pack.
```
