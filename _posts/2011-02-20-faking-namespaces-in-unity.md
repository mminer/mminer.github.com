---
layout: post
title: Faking Namespaces in Unity
---

> Fake it until you make it. Or until somebody else makes it.
> <small>Alfred Mirek</small>

Recently the devilishly handsome Nick Breslin [asked](http://twitter.com/#!/KegOfGlory/status/34843233922060288) about an alternative to namespaces in Unity. Namespaces are a familiar concept to C# programmers that solve the problem of naming collisions, but Unity has yet to support them. The [documentation](http://unity3d.com/support/documentation/ScriptReference/index.Writing_Scripts_in_Csharp.html) promises that this limitation "will be removed in a future version," but don't hold your breath. You need to breathe.

If you're unaware of what namespaces are, you probably won't care about this post. If you're a Unity programmer familiar with the construct, you still probably won't find it overly enthralling. Heck, even I have difficulty mustering enthusiasm about the subject. The reason is that you're unlikely to encounter naming collisions as a game developer. The issue arises when building libraries to be used by other developers. Distribute a class named `Player` in your .unitypackage and watch as disgruntled developers ask why Unity's console shouts at them. If you're distributing code for others to incorporate into their game, it's important that it doesn't require them to rename their existing scripts.

The solution I offered to Mr. Breslin was the use of nested classes. That is, make your classes the children of a single parent class.

{% highlight csharp %}
public class SuperAI {
	public class Pathfinding {
		...
	}

	public class BehaviourTree {
		...
	}
}
{% endhighlight %}

To separate each class into separate files for better organization, use C#'s [partial classes](http://msdn.microsoft.com/en-us/library/wa80x488(v=vs.80).aspx#Y288).

{% highlight csharp %}
// SuperAIPathfinding.cs
public partial class SuperAI {
	public class Pathfinding {
		...
	}
}
{% endhighlight %}

{% highlight csharp %}
// SuperAIBehaviourTree.cs
public partial class SuperAI {
	public class BehaviourTree {
		...
	}
}
{% endhighlight %}

This allows developers implementing your library to have their own `Pathfinding` class. Unfortunately, it's an imperfect solution. If one of the nested classes inherits from `MonoBehaviour`, you are unable to attach it to a game object. Also, Unity prevents two files from having the same name, so if your library contains a file named Pathfinding.cs and the developer has a script named identically, Unity's compiler will shake its fist and curse rudely. Furthermore, you can't simply jam a `using` keyword at the top of your class and have the child classes available without the `SuperAI` accessor.

Of course, other options are available. For one, your library can be distributed in assembly (DLL) form and use actual namespaces. But again, classes are unable to inherit from `MonoBehaviour` and be used as a component. Also, your code becomes unmodifiable once it's in DLL form, which may be undesirable if you want to give developers the ability to make their own tweaks.

The simplest solution, and perhaps the most obvious, is to prefix all class names with the name of your library.

{% highlight csharp %}
public class SuperAIPathfinding {
	...
}

public class SuperAIBehaviourTree {
	...
}
{% endhighlight %}

When I worked at OverInteractive Media, this is how we avoided naming collisions in dimeRocker's client package. With classes like `Util` and `Debug`, we needed to ensure that our naming decisions wouldn't cause grief for developers using the service. We simply prefixed every class name with "dr"; no nested classes, partial classes, or awkwardly named files. We needed scripts that inherited from `MonoBehaviour` and which could be modified by the developer, so this option was also our only one.

As usual, the simplest solution is often the most effective. While faking namespaces through a combination of nested and partial classes might strike your fancy, simply giving your classes unique names might be the best choice for keeping those dastardly naming collisions to a minimum.
