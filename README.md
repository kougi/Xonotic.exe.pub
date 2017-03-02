# Xonotic.exe.pub
Mapinfo and Hookrace files


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


//to set a size, we draw a rectangle.
"mins" "-100 -100 0" // Start of the rectangle, use minus from current location so that origin stays in center, though Z only goes up, from 0 to 250 here
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

