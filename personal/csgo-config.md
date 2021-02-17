---
Title: CS:GO config
Description: 
Date: 28-07-2020
Tags:
Editor: markdown
---

TODO: update this

# CS:GO Config

Autoexec for Counter Strike Global Offensive (CS:GO) including scripts and binds. Most recent version can be found on [my personal github](https://github.com/emielvanseveren/csgo-config).


**last modified on: 05/04/2020.**

## Autoexec (main)

```

clear

echo "------------------------"
echo
echo "Initializing CS:GO config"
echo
echo "------------------------"
echo

// Remove these modules by putting double slashes in front of the lines.
exec controls.cfg
exec crosshair.cfg
exec misc.cfg
exec network.cfg
exec trashtalk.cfg
exec video.cfg
exec viewmodel.cfg

host_writeconfig

echo "------------------------"
echo
echo "Finalizing CS:GO config"
echo
echo "------------------------"

echo "Aliases:"
echo
echo "aim_botz  - Load the aim_botz map"
echo "recoil    - Load the recoial training map"
echo "10man     - Connect to (private) 10 man server"
echo "training  - Run commands for grenade training"
echo "d         - Disconnect from current server."
echo
echo "------------------------"
```


## Controls

```
// control settings
// ----------------

echo "Initializing control settings"

bind "z" "+forward"                       // Bind z to forward movement.
bind "s" "+moveback"                      // Bind s to backwards movement
bind "q" "+moveleft"                      // Bind q to left movement.
bind "d" "+moveright"                     // Bind d to right movement.

bind "c"  "use weapon_smokegrenade"       // Bind c to smoke.
bind "f"  "use weapon_flashbang"          // Bind f to flashbang.
bind "g"  "use weapon_hegrenade"          // Bind g to grenade.

bind "h"  "+lookatweapon"                 // Bind j to inspect weapon.
bind "p"  "holdpos"                       // Bind p to 'hold position', to position bots at your current position.
bind "n"  "say .noclip; noclip"           // Bind n to noclip. say noclip in chat.
bind shift "+speed; r_cleardecals"        // Remove bullet impacts and blood when pressing shift.

// Drop bomb quickly
bind "x" +dropBomb
alias +dropBomb "use weapon_knife; use weapon_c4; drop"
alias -dropBomb "slot2; slot1"

// Voice chat toggle
bind "w" "voice_chat"
alias "voice_chat" "chat_0"
alias "chat_1" "voice_scale 1; say_team Team is unmuted.; playvol buttons\blip1 0.5; alias voice_chat chat_0"
alias "chat_0" "voice_scale 0; say_team Team is muted.; playvol buttons\blip2 0.5; alias voice_chat chat_1"

// Jumpthrow
alias "+jumpthrow" "+jump;-attack"
alias "-jumpthrow" "-jump"
bind "mouse4" "+jumpthrow;"       // bind to scroll click.

// Avoid disconnecting while afk
bind "ins" "+left"                        // Bind insert to left movement.
bind "del" "+right"                       // Bind del to right movement.
```

## Crosshair

```
// crosshair settings
// ------------------

echo "Initializing crosshair"

cl_crosshair_drawoutline                            "0"
cl_crosshair_dynamic_maxdist_splitratio             "0.35"
cl_crosshair_dynamic_splitalpha_innermod            "1"
cl_crosshair_dynamic_splitalpha_outermod            "0.5"
cl_crosshair_dynamic_splitdist                      "1"
cl_crosshair_friendly_warning                       "0"
cl_crosshair_outlinethickness                       "0.000000"
cl_crosshair_sniper_show_normal_inaccuracy          "1"
cl_crosshair_sniper_width                           "1"
cl_crosshair_t                                      "0"
cl_crosshairalpha                                   "255.000000"
cl_crosshaircolor                                   "5"
cl_crosshaircolor_b                                 "0"
cl_crosshaircolor_g                                 "255.000000"
cl_crosshaircolor_r                                 "0.000000"
cl_crosshairdot                                     "0"
cl_crosshairgap                                     "-2.584610"
cl_crosshairgap_useweaponvalue                      "0"
cl_crosshairsize                                    "1.532686"
cl_crosshairstyle                                   "4"
cl_crosshairthickness                               "0.922466"
cl_crosshairusealpha                                "1"
cl_fixedcrosshairgap                                "3"
```

```
// misc settings
// -------------

echo "Initializing misc settings"


net_graph                                 1                 // Show net_graph
developer                                 "1"               // Developer message severity. 0, least severe. 7 max severe.
con_filter_text                           "Damage given: "  // Produced text when console filter is enabled.
con_filter_text_out                       "Player:"         // Filter messages containing the word player.
con_filter_enable                         "2"               //

// Mouse
m_rawinput                                "1"               // Input taken directly from mouse. Operating system settings (acceleration, delay) will not come into play.
m_customaccel                             "0"               // Disable mouse acceleration.
m_customaccel_exponent                    "0"               // what speed you need to be moving your mouse before custom mouse acceleration kicks in.
m_mousespeed                              "0"               // Disable windows mouse acceleration.
m_mouseaccel1                             "0"               // Disable mouse acceleration.
m_mouseaccel2                             "0"               // Disable mouse acceleration.

// Audio
snd_music_volume                          "0.8"             // Master music volume level.
snd_deathcamera_volume                    "0"               // Music in deathcamera.
snd_mapobjective_volume                   "0"               // Music that starts when bomb is planted.
snd_menumusic_volume                      "0"               // Music in main menu.
snd_roundend_volume                       "0"               // Music when round ends.
snd_roundstart_volume                     "0"               // Music when round starts.
snd_tensecondwarning_volume               "0.2"             // 10 second bomb music timer (actually 9.7 seconds) (Recommended on).
voice_enabled                             "1"               // Enable voice of other players.
voice_scale                               "0.5"             // Volume of voice communication. (i.e. how load other payers microphones are).
windows_speaker_config                    "1"               // Headphone audio output.
lobby_voice_chat_enabled                  "0"               // Disable voice chat while waiting in a lobby.
snd_mute_losefocus                        "1"               // Mute game while alt-tabbed.
snd_legacy_surround                       "0"               // Emulate surround sound.
snd_mixahead                              "0.05"            // Sound delay. (recommended)

// Dificult to explain.
// Footsteps and bomb plants are better audible but player his distance is harder to predict.
snd_headphone_pan_exponent                "2"
snd_headphone_pan_radial_weight           "2"


// Misc
cl_join_advertise                         "2"               // Let your friends join your community server without an invitation.
cl_disablehtmlmotd                        "1"               // Disable HTML message of the day in the client.
cl_teammate_colors_show                   "2"               // Display color letters over teammate color in the radar in competitive.
cl_use_opens_buy_menu                     "0"               // Disables E opening the buy menu.
cl_showloadout                            "1"               // Always show your loadout hud.
cl_loadout_colorweaponnames               "1"               // Give weapon a color while on the ground.
cl_disablefeezecam                        "1"               // Disable replay of death in certain servers, to reduce tilt when killed.
mm_csgo_community_search_players_min      "7"               // Minimum amount of actual players on servers Valve connects you to. No more bot only servers.
mm_dedicated_search_maxping               "50"              // Max ping for matchmaking games.
gameinstructor_enable                     "0"               // Disable game instructor messages (i.e. showing location of bomb).

// Aliases
// type when of these while queueing for a game to practice while waiting.
// Make sure you are subscribed to these maps.

alias "aim_botz"  "map workshop\243702660\aim_botz"
alias "recoil"    "map workshop\419404847\recoil_master"
alias "10man"     "connect 149.202.87.44:11201; password 10man"
alias "d"         "disconnect"                                  // type d in console to disconnect
alias "training"  "exec training.cfg"
```

## Network
```
// network settings
// ----------------

echo "Initializing network settings"


// increases the number of updates send to the server per second. Allowing for lower latency if you have sufficient bandwidth.
cl_cmdrate                    "128"
cl_updaterate                 "128"

rate                          "786432"        // Control how much bandwidth CS:GO uses.
                                              // .5   Mbps - rate 62500
                                              // 1.0  Mbps - rate 125000
                                              // 1.5  Mbps - rate 187500
                                              // 1.57 Mbps - rate 196608 (default)
                                              // 2.0  Mbps - rate 250000
                                              // 2.5  Mbps - rate 312500
                                              // 3.0  Mbps - rate 375000
                                              // 3.5  Mbps - rate 437500
                                              // 4.0  Mbps - rate 500000
                                              // 4.5  Mbps - rate 562500
                                              // 5.0  Mbps - rate 625000
                                              // 5.5  Mbps - rate 687500
                                              // 6.0  Mbps - rate 750000
                                              // 6.2  Mbps - rate 786432 (max)

cl_interp                     "0.031"             // No interpolation or 'smoothing' of other player positions.
cl_interp_ratio               "1"             // they are more accurately positioned on your screen but may move weirdly if lagging.
```

## Training

```// training settings
// -----------------

echo "Initializing training settings"

clear;
mp_autoteambalance "0"
mp_limitteams "0"
mp_startmoney 16000"
mp_freezetime "0"
mp_buytime "9999"
mp_roundtime "9999"
sv_cheats "1"
sv_infinite_ammo "1"
mp_restartgame "1"
mp_respawn_immunitytime "10"
bot_chatter "off"
sv_grenade_trajectory "1"
sv_ignoregrenaderadio "1"
mp_buy_anywhere "1"
mp_friendlyfire "0"
mp_randomspawn "1"
mp_respawnwavetime_ct "1"
mp_respawnwavetime_t "1"
mp_free_armor "1"
mp_warmup_end
mp_t_default_primary "weapon_ak47"
mp_ct_default_primary "weapon_m4a1"
mp_t_default_secondary "weapon_p250"
mp_ct_default_secondary "weapon_fn57"
mp_roundtime_defuse 99999
bot_kick
echo "-----------------------------------"
echo
echo "Enabled training mode!"
echo
echo "-----------------------------------"
```

## Trashtalk

```
// trashtalk settings
// ------------------

echo "Initializing trashtalk settings"

alias "trashtalker" "trashtalk1"
alias "trashtalk1" "say Maybe if you stopped taking loads in the mouth you wouldn't be so salty; alias trashtalker trashtalk2;
alias "trashtalk2" "say You guys were ecoing as well?; alias trashtalker trashtalk3;
alias "trashtalk3" "say My dead dad has better aim than you. It only took him one bullet..; alias trashtalker trashtalk4;
alias "trashtalk4" "say Guys, if we want to win this, stop writing fucking Klingon, can't understand shit.; alias trashtalker trashtalk5;
alias "trashtalk5" "say Yo mama so fat when she plays overpass you can shoot her on mirage; alias trashtalker trashtalk6;
alias "trashtalk6" "say Don't be a loser, buy a rope and hang yourself; alias trashtalker trashtalk7;
alias "trashtalk7" "say Go have a 3 sum with your sister and your cousin you fucking hill billy redneck; alias trashtalker trashtalk8;
alias "trashtalk8" "say Stop playing like KQLY why cant you play more like tarik; alias trashtalker trashtalk9;
alias "trashtalk9" "say The only thing you carry is an extra chromosome.; alias trashtalker trashtalk10;
alias "trashtalk10" "say Is this casual?? I have 16k...; alias trashtalker trashtalk11;
alias "trashtalk11" "say I'm not racist... I just hate black people!; alias trashtalker trashtalk12;
alias "trashtalk12" "say If you were a CSGO match, your mother would have a 7day cooldown all the time, because she kept abandoning you.; alias trashtalker trashtalk13;
alias "trashtalk13" "say I bet you're the type of dude that likes it when your toilet paper breaks and your finger slides up your asshole.; alias trashtalker trashtalk14;
alias "trashtalk14" "say Your shots are like a bad girlfriend: No Head; alias trashtalker trashtalk15;
alias "trashtalk15" "say I PLAY WITH A RACING WHEEL; alias trashtalker trashtalk16;
alias "trashtalk16" "say Do you make eye-contact when you're fucking your dad in the ass?; alias trashtalker trashtalk17;
alias "trashtalk17" "say You look like you have parkinsons you shake and bake fuck-knuckle.; alias trashtalker trashtalk18;
alias "trashtalk18" "say We may have lost the game, but at the end of the day we, unlike you, are not russians; alias trashtalker trashtalk19;
alias "trashtalk19" "say They do not deserve like this, they do not deserve for rekt.; alias trashtalker trashtalk20;
alias "trashtalk20" "say Internet Explorer is faster than your reactions; alias trashtalker trashtalk21;
alias "trashtalk21" "say I kissed your mom last night. Her breath was globally offensive; alias trashtalker trashtalk22;
alias "trashtalk22" "say How'd you hit the ACCEPT button with that aim?; alias trashtalker trashtalk23;
alias "trashtalk23" "say Imagine your potential if you didn't have Parkinsons.; alias trashtalker trashtalk24;
alias "trashtalk24" "say Buy sound next time; alias trashtalker trashtalk25;
alias "trashtalk25" "say You don't deserve to play this game. Go back to playing with crayons and shitting yourself; alias trashtalker trashtalk26;
alias "trashtalk26" "say Hey mate, what controller are you using?; alias trashtalker trashtalk27;
alias "trashtalk27" "say With aim like that, I pity whoever has to clean the floor around your toilet.; alias trashtalker trashtalk28;
alias "trashtalk28" "say How do you change your difficulty settings? My CSGO is stuck on easy; alias trashtalker trashtalk29;
alias "trashtalk29" "say I would call you AIDS but at least AIDS gets kills.; alias trashtalker trashtalk30;
alias "trashtalk30" "say You can't even carry groceries in from the car; alias trashtalker trashtalk31;
alias "trashtalk31" "say Don't be upsetti, have some spaghetti; alias trashtalker trashtalk32;
alias "trashtalk32" "say Nice $4750 decoy; alias trashtalker trashtalk33;
alias "trashtalk33" "say At least I don't live in the world's most corrupt country; alias trashtalker trashtalk34;
alias "trashtalk34" "say How did you change your difficulty settings? My CS:GO is stuck on easy; alias trashtalker trashtalk35;
alias "trashtalk35" "say Oops, I must have chosen easy bots by accident; alias trashtalker trashtalk36;
alias "trashtalk36" "say I'm the reason your dad's gay.; alias trashtalker trashtalk37;
alias "trashtalk37" "say Dude you're so fat you run out of breath rushing B; alias trashtalker trashtalk38;
alias "trashtalk38" "say Are you one of those special kids?; alias trashtalker trashtalk39;
alias "trashtalk39" "say Bro you couldn't hit an elephant in the ass with a shotgun with aim like that; alias trashtalker trashtalk40;
alias "trashtalk40" "say Did you grow up near by Tschernobyl or why are you so toxic?; alias trashtalker trashtalk41;
alias "trashtalk41" "say You have a reaction time slower than coastal erosion; alias trashtalker trashtalk42;
alias "trashtalk42" "say You sound like your parents beat each other in front of you; alias trashtalker trashtalk43;
alias "trashtalk43" "say I thought I already finished chemistry.. So much NaCl around here...; alias trashtalker trashtalk44;
alias "trashtalk44" "say server cvar 'sv_rekt' changed to 1.; alias trashtalker trashtalk45;
alias "trashtalk45" "say I'd say your aim is cancer, but cancer kills.; alias trashtalker trashtalk46;
alias "trashtalk46" "say CRY HERE ---> \__/ <--- Africans need water; alias trashtalker trashtalk47;
alias "trashtalk47" "say CS:GO is too hard for you m8 maybe consider a game that requires less skill, like idk.... solitaire; alias trashtalker trashtalk48;
alias "trashtalk48" "say is that a decoy, or are you trying to shoot somebody?; alias trashtalker trashtalk49;
alias "trashtalk49" "say Sorry, I don't speak star wars; alias trashtalker trashtalk50;
alias "trashtalk50" "say Hey man, dont worry about being bad. It's called a trashCAN not a trashCAN'T.; alias trashtalker trashtalk51;
alias "trashtalk51" "say Is your monitor on?; alias trashtalker trashtalk52;
alias "trashtalk52" "say you must be fat because you have a nice voice, and the air needs enough space in your lungs to articulate the sound right; alias trashtalker trashtalk53;
alias "trashtalk53" "say Kick your teammate, he's flooring.; alias trashtalker trashtalk54;
alias "trashtalk54" "say Even Noah can't carry these animals; alias trashtalker trashtalk55;
alias "trashtalk55" "say Id rather rub my dick with sandpaper than play with you guys; alias trashtalker trashtalk56;
alias "trashtalk56" "say Watching you play is making my brain cells want commit suicide.; alias trashtalker trashtalk57;
alias "trashtalk57" "say If I were to commit suicide, I would jump from your ego to your elo.; alias trashtalker trashtalk58;
alias "trashtalk58" "say I'm not trash talking, I'm talking to trash.; alias trashtalker trashtalk59;
alias "trashtalk59" "say Sell your computer and buy a Wii; alias trashtalker trashtalk60;
alias "trashtalk60" "say deranking?; alias trashtalker trashtalk61;
alias "trashtalk61" "say This guy is more toxic than the beaches at Fukushima; alias trashtalker trashtalk62;
alias "trashtalk62" "say You're the reason the gene pool should have a life guard; alias trashtalker trashtalk63;
alias "trashtalk63" "say Isn't it uncomfortable playing Counterstrike in the kitchen?; alias trashtalker trashtalk64;
alias "trashtalk64" "say Even if you would play tetris you would tie up; alias trashtalker trashtalk65;
alias "trashtalk65" "say You dropped that bomb just like your mom dropped you on your head as a kid; alias trashtalker trashtalk66;
alias "trashtalk66" "say How much did you tag that wall for??; alias trashtalker trashtalk67;
alias "trashtalk67" "say You only killed me because I ran out of health...; alias trashtalker trashtalk68;
alias "trashtalk68" "say You must be russian, I smell your drunk mom; alias trashtalker trashtalk69;
alias "trashtalk69" "say You Polish fuck, Hitler should had killed your family; alias trashtalker trashtalk70;
alias "trashtalk70" "say Rest in spaghetti never forgetti; alias trashtalker trashtalk71;
alias "trashtalk71" "say Stop buying an awp you $4750 Decoy; alias trashtalker trashtalk72;
alias "trashtalk72" "say Which one of your 2 dads taught you how to play CS?; alias trashtalker trashtalk73;
alias "trashtalk73" "say Did you learn your spray downs in a bukkake video?; alias trashtalker trashtalk74;
alias "trashtalk74" "say Shut up kid and talk to me when your balls have reached the bottom of your spiderman underwear!; alias trashtalker trashtalk75;
alias "trashtalk75" "say You're the human equivalent of a participation award.; alias trashtalker trashtalk76;
alias "trashtalk76" "say If i wanted to listen to an asshole I would fart; alias trashtalker trashtalk77;
alias "trashtalk77" "say You shoot like an AI designed by a 10 year old; alias trashtalker trashtalk78;
alias "trashtalk78" "say Yo momma so fat, she gets stuck at long doors.; alias trashtalker trashtalk79;
alias "trashtalk79" "say mad cuz bad; alias trashtalker trashtalk80;
alias "trashtalk80" "say I'm surprised you've got the brain power to keep your heart beating; alias trashtalker trashtalk81;
alias "trashtalk81" "say Options -> How To Play; alias trashtalker trashtalk82;
alias "trashtalk82" "say Did you know that csgo is free to uninstall?; alias trashtalker trashtalk83;
alias "trashtalk83" "say ez katka 8); alias trashtalker trashtalk84;
alias "trashtalk84" "say You can feel the autism; alias trashtalker trashtalk85;
alias "trashtalk85" "say if I wanted a comeback, I'd get it off your moms face; alias trashtalker trashtalk86;
alias "trashtalk86" "say My knife is well-worn, just like your mother; alias trashtalker trashtalk87;
alias "trashtalk87" "say Who are you sponsored by? Parkinson's?; alias trashtalker trashtalk88;
alias "trashtalk88" "say I thought I put bots on hard, why are they on easy?; alias trashtalker trashtalk89;
alias "trashtalk89" "say Shut up, I fucked your dad.; alias trashtalker trashtalk90;
alias "trashtalk90" "say Your mom is so fat when she boosts she teamkills; alias trashtalker trashtalk91;
alias "trashtalk91" "say LISTEN HERE YOU LITTLE FUCKER, WHEN I WAS YOUR AGE, PLUTO WAS A PLANET!; alias trashtalker trashtalk92;
alias "trashtalk92" "say Like what your mother did to you, can I get a drop?; alias trashtalker trashtalk93;
alias "trashtalk93" "say You're almost as salty as the semen dripping from your mum's mouth; alias trashtalker trashtalk94;
alias "trashtalk94" "say You could not pre-fire a marching band full of elephants; alias trashtalker trashtalk95;
alias "trashtalk95" "say I could swallow bullets and shit out a better spray than that; alias trashtalker trashtalk96;
alias "trashtalk96" "say At least my country has indoor plumbing; alias trashtalker trashtalk97;
alias "trashtalk97" "say Safest place for us to stand is in front of your gun; alias trashtalker trashtalk98;
alias "trashtalk98" "say Your nans like my ak vulcan, battle-scarred; alias trashtalker trashtalk99;
alias "trashtalk99" "say If you want to play against enemies of your skill level just go to the main menu and click 'Offline with Bots'; alias trashtalker trashtalk100;
alias "trashtalk100" "say FYI: Warmup is over already!; alias trashtalker trashtalk101;
alias "trashtalk101" "say You have the reaction time of a dead puppy.; alias trashtalker trashtalk102;
alias "trashtalk102" "say Bhopped to your mom's house last Sunday. Top kek; alias trashtalker trashtalk103;
alias "trashtalk103" "say You define autism; alias trashtalker trashtalk104;
alias "trashtalk104" "say If this guy was the shooter harambe would still be alive; alias trashtalker trashtalk105;
alias "trashtalk105" "say Was that your spray on the wall or are you just happy to see me?; alias trashtalker trashtalk106;
alias "trashtalk106" "say Theres more silver here than in the cutlery drawer; alias trashtalker trashtalk1;
bind ";" "trashtalker"
```

## Video

```

// video/fps commands
// ------------------

echo "Initializing video settings"

cl_forcepreload                 "1"               // Preload the whole map and sound.
cl_downloadfilter               "nosound"         // Do not preload sounds.
mat_queue_mode                  "2"               // Forcing your CPU to use multi-threaded mode.
r_eyemove                       "0"               // Disable eye movement.
r_eyeshift_x                    "0"               // Disable eye movement x-angle.
r_eyeshift_y                    "0"               // Disable eye movement y-angle.
r_eyeshift_z                    "0"               // Disable eye movement z-angle.
r_dynamic                       "1"               // Gunfire lightning, spot enemies easier.
r_drawtracers_firstperson       "1"               // See bullets fly when u spray.
fps_max                         "500"             // Static max is better than 0 for some loading times, sometimes.
fpx_max_menu                    "500"             // Max fps while in main menu.
mat_setvideomode                1920 1080 0       // Resolution <width> <height> <windowed>
mat_monitor_gamma               "1.6"             // Brightness, 2 is default.
```

## Viewmodel

```
  
// viewmodel settings
// ------------------

echo "Initializing viewmodel"

// Reduce gun and scope shifting/bobbing when moving
cl_bob_lower_amt                    "5.000000"
cl_bobamt_lat                       "0.100000"
cl_bobamt_vert                      "0.100000"
cl_bobcycle                         "0.98"

cl_viewmodel_shift_left_amt         "0.500000"
cl_viewmodel_shift_right_amt        "0.250000"
viewmodel_fov                       "68"
viewmodel_offset_x                  "1.25"
viewmodel_offset_y                  "0.75"
viewmodel_offset_z                  "-1.8"
viewmodel_presetpos                 "0"

// HUD settings
hud_scaling                         "1"             // Maintain default size.
hud_showtargetid                    "0"             // If set to 1, crosshair will change color when on target.
cl_hud_healthammo_style             "0"             // Show a bar next to health.
cl_hud_bomb_under_radar             "0"             // Hide bomb icon under radar while carrying the bomb.
cl_hud_playercount_pos              "1"             // Scoreboard position. 1 top, 0 bottom.
cl_hud_playercount_showcount        "0"             // If set to 0, show avatars, if set to 1 show amount of players alive.
cl_hud_background_alpha             "0.25"          // Make hud slightly transparent.
cl_hud_color                        "4"             // purple hud.

// hud colors
//  0  = default
//  1  = white        2  = light blue
//  3  = dark blue    4  = purple
//  5  = red          6  = orange
//  7  = yellow       8  = green
//  9  = green/aqua   10 = pink
```

