# Unreal Metasound Footsteps responding to Materials
This tutorial will cover the basics of getting footsteps to respond to materials and linking this into Metasounds.

## Create your Material Properties
The first part of this process consists of defining abstract materials that we’ll use in our project. This will then be used to create new `Physical Material` blueprints that can then be assigned our actual materials that will be used to texture our floors.

1. Make sure you have the starter content assets loaded in your project (we’ll use these to grab some materials). If you don’t have them, you can add them using the “Import” button in the Content Browser.
2. Open your Project Settings, and search for “Surface”. Create two new Physical Surfaces, one named `Grass` and one named `Stone`.
3. Open your Content Browser at the top level `Content` directory. Right click and make two new Physics > Physical Material instances. Name one `Grass_Material` and one `Stone_Material`.
4. Double click on your new `Grass_Material` and change its `Physical Properties > Surface Type` to `Grass`. The only options in this dropdown menu will be the two that you added to your Project Settings (+ Default).
5. Do the same as step 4 for your `Stone_Material`.

## Applying our material abstractions to our Mesh Materials
Next we’re going to create two new materials that we will apply to our floors; these materials will both texture the floors and also let Unreal know that we’re stepping on grass or stone based on the `Physical Material` properties.

1. In the starter content folder of the content browser, find a material to represent grass, such as `M_Ground_Grass`. Right-click on it and choose `Create Material Instance` from the top of the contextual menu. Rename this new instance `GRASS`. By creating a new instance of this material, we can customize it while saving the original for future potential use.
2. Double click on your new `GRASS` material. In the `Details` panel, set `General > Phys_Material` to be `Grass_Material`
3. Repeat steps 1 & 2 for Stone.
4. OK, now we’re ready to apply these to meshes in our level! Drag `GRASS` on to the main floor of our level, and `STONE` onto one of the platforms. You’ll notice that the textures are scaled inappropriately; you can double click on the materials and edit their blueprints to change the UV values if you like but we won’t cover that here.

## Adding notifications to our footsteps
Go into the `Content > Characters > Animations > MF_Run_Fwd` Blueprint. For each footfall, add a Skeleton Notify > `l_foot_plant` or `r_foot_plant` notification. You can create Skeleton Notifies by right-clicking into the animation timeline.

## Add sounds to our main animation Blueprint
OK, here’s we we bring everything together. This is a fairly complex blueprint, so I’ve attached a screenshot for reference. Before you begin this part, make sure you have a Metasound to use for footstep sound effects.

1. Navigate to `Content > Mannequins > Animations` and then select either the `ABP` blueprint for Quinn or Manny depending on which one your project uses. Double click it to begin editing it.
2. Find a spot in the Blueprint that can accept a large number of nodes. Start of your script by right clicking and searching for `AnimNotify_l_foot_plant`. Do the same for the right foot plant as well. Note that we could potentially trigger different sounds for different feet at this point.
3. Next we need to determine what type of surface the player character is currently stepping on. We can do this using a *line trace*, which lets us trace a line from one point to another and see what we hit along the way (if anything). In this case we want to start at the players current position, and then travel down along the z-axis to see what floor material we hit. Right-click and choose the `Line Trace By Channel` node. Connect both of your animation notification nodes to its execution input (the top one).
4. Now we want to get the player characters position. Right-click and choose the `Get Player Character` node. Drag a pin off the return value and choose `Get Actor Location`. Connect the return value of the Actor Location to the `Start` input of our line trace node. 
5. OK, now we have our starting point for the trace established. To create the ending point, drag a pin from  `Get Actor Location > Return Value` and type the minus key (-). Because the actor location is a vector, this will bring up a three-member vector. Set the Z value (the last one in the list) to be 150. This will create an end point that is 150 centimeters below the current position of our player character… if anything is struck along that path it will be returned. Connect the output of our subtracted vector to the `End` input of our `Line Trace By Channel` node.
6. OK, next we want to see if we hit something! Drag a pin off the execution output of our line trace node and search for `Branch`. This will let us only carry out an action if a given condition is true. Our line trace node has a return value that is set to True or False depending on whether or not the trace encountered a surface. Connect the `Return Value` to the `Condition` of our Branch. 
7. Drag a pin off the `True` output of our branch and create a `Spawn Sound at Location` node. Select your Metasound for the `Sound` input. 
8. Drag a pin off of the `Out Hit` output from our line trace. Choose `Break Hit Result`. This node will give us a variety of information about our hit test. Take the `Location` output pin of the `Break Hit Result` node and connect it to the `Location` input of our `Spawn Sound at Location` node. 
9. Compile and save your Blueprint. Test the level. You should now have sound for your footfalls… if you don’t this would be a good time to debug. But the sound still doesn’t respond to our materials… next we’ll edit our Metasound briefly, but we’ll come back to this animation blueprint.
10. Go into your Metasound and create a new input named `Material`. Connect this input to some part of your Metasound patch so that it can control the generated sound… the frequency of an oscillator would be an easy option. Set a default value and a min / max.
11. Back to your main animation Blueprint. Drag a pin off of the `Return Value` from your `Spawn Sound at Location` node. This will create a reference to your Metasound. Select the `Set Float Parameter` node (assuming you set your Metasound Material input to be a float, otherwise choose an appropriate node). For the `In Name` input, choose `Material`, the name you gave your input in your Metasound patch. Specify a value to set the input to. Compile, save, and test! You should hear the change to your Metasound.
12. OK, the last thing we need to get is grab the type of surface our line trace hit, and then change the `Material` input to our metasound based on that type. Drag a pin from the `Out Hit` output of our line trace node and create a `Get Surface Type` node. Drag a pin from the resulting `Return Value` and create a `Switch on EPhysicalSurface`. You'll see that this node has execution outputs for both of our materials. We’re close!!!
13. Connect the `Spawn Sound at Location` execution output to the `Switch on EPhysicalSurface` execution input.
14. Connect the `Grass` output to our `Set Float Parameter` execution input (break the existing connection to our Spawn Sound node first). Copy and paste the Set Float Parameter node and specify a different float value. Connect the `Stone` execution output to this node.
15. You’re done! Save, compile, and test. 

