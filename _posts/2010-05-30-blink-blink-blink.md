---
layout: post
title: Blink Blink Blink
---

> Alternating visibility of letters, you say? What a splendid invention.
> <small>Eustice P. McGargle</small>

As [promised](/2010/a-new-medium-for-the-scrolling-marquee/): a blinking text script for Unity, to bring back the glory days of Netscape Navigator. Sophistication starts here.

{% highlight csharp %}
public float interval = 1;
bool visible = true;

void Start () {
	// Start blinking immediately
	TriggerBlink();
}

void OnGUI () {
	if (!visible) {
		// Set the GUI to be invisible
		GUI.color = Color.clear;
	}

	GUILayout.Label("History is gonna change.");
}

void TriggerBlink () {
	visible = !visible;
	// Continuous loop
	Invoke("TriggerBlink", interval);
}
{% endhighlight %}
