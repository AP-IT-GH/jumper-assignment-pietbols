# jumper-assignment-pietbols

Create a new 3D project in your Unity Hub.
![image](https://user-images.githubusercontent.com/79148675/166330474-3cb803bd-4e06-4df7-87c4-6e265af83f1d.png)


Make sure you have the "ML Agents" package installed in your Package Manager.
![image](https://user-images.githubusercontent.com/79148675/166330897-250f6f60-d5fb-4b26-95ad-f31cbbb23536.png)


Now we can start by CREATING THE TRAINING AREA:

step 1: create an empty object and name it "TrainingArea"
<br>
![image](https://user-images.githubusercontent.com/79148675/166331769-d2255a61-eba0-40a4-89df-c770707b9127.png)


step 2: add a plane and rename it to "Floor"
<br>
![image](https://user-images.githubusercontent.com/79148675/166331182-ae4a4275-e806-427c-b81b-4506c3150be0.png)

make sure it has the following settings
<br>
![image](https://user-images.githubusercontent.com/79148675/166331427-93834f37-e014-47ce-a35d-1a368d52b899.png)


step 3: add a cube that will act as our Agent
<br>
![image](https://user-images.githubusercontent.com/79148675/166331950-15eb73fc-c2a0-46fb-b1ad-a0dcf2475c41.png)
<br>

add a decision requester, behaviour parameters and Ray perception sensor 3D 
<br>
![image](https://user-images.githubusercontent.com/79148675/166338352-f482c5c4-18f7-4216-b9be-bbba20f139b3.png)
<br>
they can be found as follows:
press this button in the Inspector of the Agent
<br>
![image](https://user-images.githubusercontent.com/79148675/166338494-a3b04f2f-8bed-4295-a385-1146443a1211.png)
<br>
type, then click, and the functionality is added
<br>
![image](https://user-images.githubusercontent.com/79148675/166338705-2678c9f4-f73f-458b-a626-6097450de576.png)




these are its basic settings
<br>
![image](https://user-images.githubusercontent.com/79148675/166332089-9a8ecbdc-fff8-4413-a095-abb4fa644d9b.png)


It is important to place it a little above the floor, as you can see by the positional Y-value of 0.5


step 4: add another cube
<br>
![image](https://user-images.githubusercontent.com/79148675/166331950-15eb73fc-c2a0-46fb-b1ad-a0dcf2475c41.png)


this cube will serve as the spawner that produces bad 'targets' and good 'powerups'

Here you can see the basic settings
<br>
![image](https://user-images.githubusercontent.com/79148675/166332729-a5b6d570-0144-46a4-9efe-30bccce04ad2.png)

step 5: make a prefab from what we've made this far

this can be done by selecting the entire TrainingArea in the Hierarchy and drag it into the 'Prefabs' folder under your projects' assets.

step 6: create a powerup from a sphere
<br>
![image](https://user-images.githubusercontent.com/79148675/166333399-f0fae3e6-78a8-4e2c-92c4-ef9197388a53.png)

these are its basic settings (except for the "start moving script)
<br>
![image](https://user-images.githubusercontent.com/79148675/166333531-02a9e490-ed89-49df-aad4-6165dd6511d3.png)

Drag it to the prefabs folder to create a prefab

step 7: create the target by adding a new cube
with these settings you can make a prefab from it
<br>
![image](https://user-images.githubusercontent.com/79148675/166333692-6dcec7b8-0a3b-42d4-9285-18b9f83e5803.png)


We will add the target and powerup from steps 6 & 7 later on to the TrainingArea prefab through scripts.


SCRIPTS

step 8: Spawning objects with the spawner object we created in step 4

create a new script
<br>
![image](https://user-images.githubusercontent.com/79148675/166335182-4f2d4418-6e3b-424b-929d-0b41595cd8a6.png)

let's start by making the enemy (target) and the powerup available in the scipt
<br>
![image](https://user-images.githubusercontent.com/79148675/166335565-df667aa4-c157-48d5-a2a3-f1092da61384.png)


we define the time between spawns like this
<br>
![image](https://user-images.githubusercontent.com/79148675/166335309-2b10c232-13f2-4d93-bccd-df69ce846de1.png)

to randomly generate positive powerups or negative targets, we generate a random value
<br>
![image](https://user-images.githubusercontent.com/79148675/166335424-af33568d-a130-4943-b008-e4c9756d180a.png)

Attach this script to the spawner object

Drag the prefabs to their according names
<br>
![image](https://user-images.githubusercontent.com/79148675/166335757-6f6c4b69-c76b-4a35-ae31-d5ea56666e86.png)


step 9: moving the spawned objects
create a new script
To make sure they move at different speeds, use a script that looks like
<br>
![image](https://user-images.githubusercontent.com/79148675/166336303-12c5ba56-d1ca-47ff-a544-e67535478d9e.png)

attatch this script to the prefabs of the target and the powerup


step 10: destroying objects that don't hit the agent

We decided to go with a timer, but this can also be done by adding a wall behing the agent and check for collision with the wall
<br>
![image](https://user-images.githubusercontent.com/79148675/166336071-ca31af2d-098b-4208-be66-b9b092d631ad.png)


step 11: destroying objects that hit the agent
<br>
![image](https://user-images.githubusercontent.com/79148675/166337151-9164ce95-dc61-4ab0-b8a5-e4c071964609.png)

Attach this script to the target and the powerup.

step 12: write the script for the agent
When you create a new C# script, it's class always inherits from the Monobehaviour class by default.
This time we have to change it to "Agent"
<br>
![image](https://user-images.githubusercontent.com/79148675/166337528-d16e5f1f-6300-4e2d-9b39-649517aba590.png)

remove the start() and update() methods

To reset the position and rotation of the agent after each episode:
<br>
![image](https://user-images.githubusercontent.com/79148675/166337863-260889ca-f7c8-4d1f-b52e-ee96881534f4.png)

<br>
To make the Agent 'see', we have to tell it to make observations
<br>
![image](https://user-images.githubusercontent.com/79148675/166338954-ddc9d8d3-8087-4867-8560-23fbc5f05caf.png)

<br>
Here is where we make the Agent perform actions (in this case it jumps)
and we can set conditions that trigger rewards (positive or negative)
<br>
![image](https://user-images.githubusercontent.com/79148675/166339172-3ee45557-f578-4b23-9878-1841c993e574.png)

<br>
Before we ran our simulations, we tested it manually.
This requires the Heuristic method
<br>
![image](https://user-images.githubusercontent.com/79148675/166339454-a5310667-38e7-4160-868b-153dbce320b3.png)
<br>
don't forget to change the Behaviour Type of the Behaviour Parameters from default to heuristic (in the Agents' inspector)
<br>
Lastly, we check if the Agent gets hit by one of the spawned objects
<br>
![image](https://user-images.githubusercontent.com/79148675/166339834-f290e543-0192-4792-a4c7-1db8d11c90a6.png)
<br>
Attach this script to the Agent.

This concludes the creation of the Training Area and its scripts.
