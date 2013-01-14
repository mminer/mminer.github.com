---
layout: post
title: A New Medium for the Scrolling Marquee
---

> Letters in motion, you say? What a splendid invention.
> <small>Eustice P. McGargle</small>

Recently when reminiscing about that custodian of excellent web design that <del>is</del> was GeoCities, I decided to give the `<blink>` and `<marquee>` tags a whirl, for old time's sake. Alas, Safari refuses to recognize these bastions of 90s tastefulness. Tears splashed on my keyboard as I mourned the death of greatness.

And then a user on the Unity forums asked about scrolling text in-game, to which I enthusiastically responded. Browser manufacturers may have made every attempt to kill the non-standard HTML elements so thoughtfully introduced by Netscape and Microsoft, but they can't take away these innovations from video games. Class will live on.

{% highlight csharp %}
public string message = "Where we're going, we don't need roads.";
public float scrollSpeed = 50;

Rect messageRect;

void OnGUI () {
	// Set up message's rect if we haven't already
	if (messageRect.width == 0) {
		GUIContent label = new GUIContent(message);
		Vector2 dimensions = GUI.skin.label.CalcSize(label);

		// Start message past left side of screen
		messageRect.x      = -dimensions.x;
		messageRect.width  =  dimensions.x;
		messageRect.height =  dimensions.y;
	}

	messageRect.x += Time.deltaTime * scrollSpeed;

	// If message has moved past right side, move it back to left
	if (messageRect.x > Screen.width) {
		messageRect.x = -messageRect.width;
	}

	GUI.Label(messageRect, message);
}
{% endhighlight %}

Stay tuned for blinking text in Unity, for even greater user enjoyment.
