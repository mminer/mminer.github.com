---
layout: post
title: "Methodic: Graphically Execute Functions"
---

> Stop having boring tuna. Stop having a boring life.
> <small>Vince Offer</small>

Now available in the Unity Asset Store: the frighteningly useful [Methodic](http://u3d.as/content/matthew-miner/methodic/1Xw). This super cool mack daddy is a tool for graphically executing functions in the editor, providing an easy way to test new code and trigger actions that would otherwise be tedious to invoke. If this doesn't get your heart racing then few things will.

Let's bust out some example usage to increase the thrill level. Suppose you have a game object with a script attached. In this script you just wrote a new function `ImmenseBlast` and you want to give it a whirl. Unfortunately you need to lay down some code to execute the function, whether that be a GUI button or a trigger or a hotkey. With Methodic, no such shenanigans are necessary. On play, simply click the game object, select "ImmenseBlast" from Methodic's dropdown menu, and hit *Invoke*. The function executes. Boom.

<img src="/img/methodic.png" alt="Methodic editor window" />

Maybe your function takes some parameters? No problem friend. A form appears where you can enter values to be passed upon execution. If one of the parameters is a `Color` struct, the colour picker appears. If the function accepts a `GameObject`, drag and drop one from the Hierarchy pane. A `Transform`? Same deal. If it was any easier I'd hire Vince Offer to pitch it.

You can pick up Methodic for $10 [here](http://u3d.as/content/matthew-miner/methodic/1Xw). As always, feedback and suggestions are appreciated, particularly as this is my first foray into the wild world of the Asset Store.
