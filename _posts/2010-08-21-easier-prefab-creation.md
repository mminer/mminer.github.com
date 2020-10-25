---
title: "Easier Prefab Creation"
---

At the request of fellow code conjurer [Brad Keys](http://www.bradkeys.com/), I wrote a simple editor script for Unity that creates a prefab containing the contents of the selected game object. The new prefab bears the name of the selected game object and is placed in the project's root directory. This function is accessed from the *GameObject → Create Prefab From Selected* menu.

While setting up prefabs is a trivial task, this menu item simplifies the process somewhat. It's not perfect --- the selected game object doesn't become an instance of the newly created prefab, and an existing prefab with the same name is replaced --- but perhaps you'll find it useful if excess clicking isn't your game of golf.

Download the script [here](https://gist.github.com/mminer/975358) or contribute your own improvements at the [Unify Wiki](http://www.unifycommunity.com/wiki/index.php?title=CreatePrefabFromSelected).
