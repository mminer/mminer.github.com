---
layout: post
title: Event.Use() and Scroll Views
---

> A scroll view that tries to reveal its content, how utterly pointless.
> <small>Matthew Miner</small>

Today's Unity discovery: calling `Event.Use()` every time the `OnGUI()` function runs will cause scroll views to not work. At least, they won't respect any dimensions you set and will simply stretch to accommodate the elements contained within it. "A scroll view that tries to reveal its content, how utterly pointless." Those were my exact words.

In code form, I had something like this:

{% highlight csharp %}
Vector2 scroll;

void OnGUI () {
	scroll = EditorGUILayout.BeginScrollView(
		scroll,
		GUILayout.Width(50),
		GUILayout.Height(200));
	GUILayout.Label("I like big labels and I cannot lie.");
	EditorGUILayout.EndScrollView();

	if (Event.current.type == EventType.KeyDown) {
		Debug.Log("You've pressed a key. Righteous.");
	}

	Event.current.Use();
}
{% endhighlight %}

The scroll view is most certainly not 50 pixels wide. Moving `Event.current.Use()` inside the if statement fixes it though.

{% highlight csharp %}
if (Event.current.type == EventType.KeyDown) {
	Debug.Log("You've pressed a key. Righteous.");
	Event.current.Use();
}
{% endhighlight %}

And all is well.
