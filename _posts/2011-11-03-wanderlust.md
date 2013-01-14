---
layout: post
title: Wanderlust
---

> I went wandering.
> <small>Johnny Cash</small>

Unity developers, this post is for you. Because you're cool and I want to be your friend.

Let's say you have an NPC. You could animate that bad boy and make it stroll around in suspiciously straight lines, but that's boring and predictable. Personally I never stroll, I meander. As aggravating mall shoppers prove, random movement is always more interesting than the linear sort, so let's make your NPCs move in this manner.

First step: toss a `CharacterController` on your character game object. You want to be constantly recalculating a new direction for them, so bust out a coroutine and set it to change the target direction every second or so. The Update function constantly rotates the character towards this target direction, with the end result being an NPC that doesn't seem intent on making it to a specific location. Such behaviour is great for patrolling guards, farm animals, and the shoppers in that totally sweet mall simulation you're building (*SimMall 3000*!).

Here's the script that does this (also available in [Gist form](https://gist.github.com/1337455)). Toss it on a game object, tweak the inspector values, and watch the magic happen.

{% highlight csharp %}
using UnityEngine;
using System.Collections;

/// <summary>
/// Creates wandering behaviour for a CharacterController.
/// </summary>
[RequireComponent(typeof(CharacterController))]
public class Wander : MonoBehaviour
{
	public float speed = 5;
	public float directionChangeInterval = 1;
	public float maxHeadingChange = 30;

	CharacterController controller;
	float heading;
	Vector3 targetRotation;

	Vector3 forward
	{
		get { return transform.TransformDirection(Vector3.forward); }
	}

	void Awake ()
	{
		controller = GetComponent<CharacterController>();

		// Set random initial rotation
		heading = Random.Range(0, 360);
		transform.eulerAngles = new Vector3(0, heading, 0);

		StartCoroutine(NewHeadingRoutine());
	}

	void Update ()
	{
		transform.eulerAngles = Vector3.Slerp(transform.eulerAngles, targetRotation, Time.deltaTime * directionChangeInterval);
		controller.SimpleMove(forward * speed);
	}

	void OnControllerColliderHit (ControllerColliderHit hit)
	{
		if (hit.gameObject.tag != "Boundary") {
			return;
		}

		// Bounce off the wall using angle of reflection
		var newDirection = Vector3.Reflect(forward, hit.normal);
		transform.rotation = Quaternion.FromToRotation(Vector3.forward, newDirection);
		heading = transform.eulerAngles.y;
		NewHeading();
	}

	/// <summary>
	/// Calculates a new direction to move towards.
	/// </summary>
	void NewHeading ()
	{
		var floor = Mathf.Clamp(heading - maxHeadingChange, 0, 360);
		var ceil  = Mathf.Clamp(heading + maxHeadingChange, 0, 360);
		heading = Random.Range(floor, ceil);
		targetRotation = new Vector3(0, heading, 0);
	}

	/// <summary>
	/// Repeatedly calculates a new direction to move towards.
	/// Use this instead of MonoBehaviour.InvokeRepeating so that the interval can be changed at runtime.
	/// </summary>
	IEnumerator NewHeadingRoutine ()
	{
		while (true) {
			NewHeading();
			yield return new WaitForSeconds(directionChangeInterval);
		}
	}
}
{% endhighlight %}

I also chucked in some code in the `OnControllerColliderHit` that changes the character's direction when it stupidly runs into a wall. The final result is an AI character that wanders aimlessly around the level, going wherever its small mind desires.

<div id="unityPlayer">
	<div class="missing">
		<a href="http://unity3d.com/webplayer/" title="Unity Web Player. Install now!">
			<img style="width: 193px; height: 63px;" alt="Unity Web Player. Install now!" src="http://webplayer.unity3d.com/installation/getunity.png" />
		</a>
	</div>
</div>
<script src="http://webplayer.unity3d.com/download_webplayer-3.x/3.0/uo/UnityObject.js"></script>
<script>
function GetUnity() {
	if (typeof unityObject != "undefined") {
		return unityObject.getObjectById("unityPlayer");
	}
	return null;
}
if (typeof unityObject != "undefined") {
	unityObject.embedUnity("unityPlayer", "/files/wander.unity3d", 440, 440);
}
</script>
