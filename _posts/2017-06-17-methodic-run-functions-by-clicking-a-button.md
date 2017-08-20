---
layout: post
title:  "Methodic: Run Functions by Clicking a Button"
date:   2017-06-17
---

Ages ago I built a small Unity editor extension that makes its way into every project I fire up. In a nutshell, it allows you to run functions in a game object's components through a GUI. I recognize how excruciatingly dull that sentence is, so let me convince you that this is something you need with an example.

Suppose you're developing a Breakout clone. Each brick gets a component with an `Explode` function that, well, makes it explode.

```csharp
using UnityEngine;

class Brick : MonoBehaviour
{
    void Explode ()
    {
        // TODO: add impressive fireball
        Debug.Log("Exploding!");
        Destroy(gameObject);
    }
}
```

Nice job. Now let's test your handiwork. There are plenty of ways to run the function, but Methodic provides the easiest. Click the brick game object, open *Window > Methodic*, hit "Invoke", and voila: your brick detonates in a fiery blast.

<img src="/images/methodic.png" alt="Methodic Window">

No extra code necessary. Even groovier, if your function takes arguments, you can specify these using familiar checkboxes and text fields and colour pickers.

<img src="/images/methodic_arguments.png" alt="Methodic Window With Arguments">

Public, private, static, or instance function, Methodic runs them all. You can even execute functions while Unity's in edit mode.<sup><a href="#fn1" id="r1">[1]</a></sup> Still yawning? Perhaps a video sells it better.

<iframe width="700" height="371" src="https://www.youtube.com/embed/x9x80XV-8G8?color=white" frameborder="0" allowfullscreen></iframe>

If this looks like something your game development environment pines for (or if you simply want to make me a wealthy man), you can [purchase Methodic](https://www.assetstore.unity3d.com/en/#!/content/954) for $10 on the Unity Asset Store. I can't promise that you'll make better games with it, but you *might*, and is that an opportunity you can ignore? Not in this economy.


---

<ol class="footnotes">
    <li id="fn1">Unity complains when running functions like <code>Object.Destroy</code> that cannot be called in edit mode. This makes sense though &mdash; destructive changes are best left for play mode.<a href="#r1" class="return"></a></li>
</ol>

<small>
    Assets for my Breakout clone from [Kenney’s Puzzle Pack 2](http://www.kenney.nl/assets/puzzle-pack-2). Thanks Kenney!
</small>
