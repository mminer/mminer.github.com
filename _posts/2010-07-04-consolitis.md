---
layout: post
title: Consolitis
---

> I had my consoles removed when I was a child.
> <small>Virginia Ann Cooksey</small>

Like any self-respecting Unity developer, I monitor the contents of the Console window religiously. The editor presents a slick interface, but when it comes to keeping tabs on the warnings and exceptions output by a web player game, a trip to OS X's Console.app is necessary. I'm apparently not the only developer to suffer through this insufferable task, and in-game console windows [have](http://www.ennanzus-interactive.com/developer/DebugConsole/) [been](http://www.unifycommunity.com/wiki/index.php?title=DebugConsole) [developed](http://github.com/dimerocker/dimeRocker-Unity-Client/) to banish my inconvenience.

Unfortunately, scripts like the one linked to above require that messages be logged using a separate class. I want to continue using Unity's trusty `Debug` class and be free to drop the script into an existing project without any code changes. Luckily Unity allows logged messages to be rerouted through your own callback method using [Application.RegisterLogCallback](http://unity3d.com/support/documentation/ScriptReference/Application.RegisterLogCallback.html). Each message can be saved to a list and displayed in a GUI window when a hotkey is pressed.

For your enjoyment, I've saved [the script](https://gist.github.com/975374) I use for my own console popup window that implements such functionality. In addition to displaying debug messages, it has a few nice features like different text colours for warnings and errors as well as a "collapse" feature that will be familiar to users of the Unity console. Simply drag this script onto any game object then use the \` backquote key (this can be changed in the inspector) to invoke it when your game is playing. No code changes necessary.

Now, using the callback to show messages in a GUI window is its obvious use. Alternatively, you can send all error messages from your deployed game to a web server where they're recorded for later perusal. This might make for a great way to implement gameplay analytics. The possibilities are endless. Like a möbius strip. Almost exactly like a möbius strip.
