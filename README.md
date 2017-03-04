# Xonotic.exe.pub
Mapinfo and Hookrace files



###Setting map's game modes.
Each map has a .mapinfo file which is a basic configuration. It determines which game modes are available for each map, as well as miscellaneous settings.

For example, in order to enable a map for CTS, and disable it in other modes, it will need the following:

```
//gametype dm
//gametype ctf
//gametype ft
gametype cts
```

The parts commented out aren't required at all, as the .mapinfo used from this repo will replace the one which comes with the map, inside of its .pk3 archive. But for tidyness' sake, having the values within the .mapinfo files makes it quicker to rename a .mapinfo file, and adjust it.


###Hook race, and making maps playable.

####Quick example of adding "triggers" to work as checkpoints to maps through the .ent file:

Use the following command to save a .ent file of a map you're currently playing:

  *sv_saveentfile*

Get your current coordinates via:

  *prvm_edictget server 1 origin*

```
{
"classname" "trigger_race_checkpoint" //start
"cnt" "0" //Checkpoint number, start and finish are 0.
"targetname" "start" //unique trigger name
"origin" "-1541 -57 400" //Coordinates, X Y Z


//to set a size, we draw a rectangle. X Y and Z
"mins" "-100 -100 0" // Start of the rectangle, use minus from current location so that origin stays in center.
"maxs" "100 100 250" // Size of the rectangle. In this example, its size is 200, 200, 250
}

{
"classname" "trigger_race_checkpoint"
"cnt" "1" //increment this with each checkpoint
"targetname" "c1"
"origin" "143 -60.2701912 410"
"mins" "-100 -100 0"
"maxs" "100 100 250"

}
```

The above will create a start, a checkpoint, but no finish, so you'll need to return to start to trigger the stop.

You can view the triggers visually, by using this command while testing:

*r_showbboxes 5*

[Entity Documentation](https://dl.dropboxusercontent.com/u/18995126/entities.ent)
