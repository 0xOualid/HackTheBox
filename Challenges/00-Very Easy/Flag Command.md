# Flag Command Writeup

> Category : Web

> Embark on the "Dimensional Escape Quest" where you wake up in a mysterious forest maze that's not quite of this world. Navigate singing squirrels, mischievous nymphs, and grumpy wizards in a whimsical labyrinth that may lead to otherworldly surprises. Will you conquer the enchanted maze or find yourself lost in a different dimension of magical challenges? The journey unfolds in this mystical escape!

## Solution

First browsing http://154.57.164.79:34113 we saw a terminal style web.

```text
>> help

start Start the game
clear Clear the game screen
audio Toggle audio on/off
restart Restart the game
info Show info about the game
```

We cannot enter any command that is not in the help menu.

So let's find another way by start viewing the source code.
We found there is three JS files.

```html
  <script src="/static/terminal/js/commands.js" type="module"></script>
  <script src="/static/terminal/js/main.js" type="module"></script>
  <script src="/static/terminal/js/game.js" type="module"></script>
```

The more important one is `main.js`. After read it we found some interesting things.

First thing we found is the three first steps.

```js
if (currentCommand == 'HEAD NORTH') {
	currentStep = '2';
}
else if (currentCommand == 'FOLLOW A MYSTERIOUS PATH') {
	currentStep = '3'
}
else if (currentCommand == 'SET UP CAMP') {
	currentStep = '4'
}
```

Second thing we found is a connection between the server and API.

```js
const fetchOptions = () => {
    fetch('/api/options')
        .then((data) => data.json())
        .then((res) => {
            availableOptions = res.allPossibleCommands;

        })
        .catch(() => {
            availableOptions = undefined;
        })
}
```

Entering http://154.57.164.79:34113/api/options we found a JSON file.

```json
{
  "allPossibleCommands": {
    "1": [
      "HEAD NORTH",
      "HEAD WEST",
      "HEAD EAST",
      "HEAD SOUTH"
    ],
    "2": [
      "GO DEEPER INTO THE FOREST",
      "FOLLOW A MYSTERIOUS PATH",
      "CLIMB A TREE",
      "TURN BACK"
    ],
    "3": [
      "EXPLORE A CAVE",
      "CROSS A RICKETY BRIDGE",
      "FOLLOW A GLOWING BUTTERFLY",
      "SET UP CAMP"
    ],
    "4": [
      "ENTER A MAGICAL PORTAL",
      "SWIM ACROSS A MYSTERIOUS LAKE",
      "FOLLOW A SINGING SQUIRREL",
      "BUILD A RAFT AND SAIL DOWNSTREAM"
    ],
    "secret": [
      "Blip-blop, in a pickle with a hiccup! Shmiggity-shmack"
    ]
  }
}
```

We already have the three first steps and now we have the secret phrase which is the fourth step.

So the steps is:

```text
HEAD NORTH

FOLLOW A MYSTERIOUS PATH

SET UP CAMP

Blip-blop, in a pickle with a hiccup! Shmiggity-shmack
```

```text
HTB{D3v3l0p3r_t00l5_4r3_b35t__t0015_wh4t_d0_y0u_Th1nk??}
```

