---
layout: post
title: Dashing Coroutines for an Improved Coding Experience
---

> I've had enough of your mumbo jumbo. Unless your mumbo jumbo encompasses coroutines. Those I dig.
> <small>Kaj Gottlob</small>

After my [last](/2010/a-new-medium-for-the-scrolling-marquee/) [two](/2010/blink-blink-blink/) borderline useless posts, perhaps today's code snippet will be more valuable. I'm optimistic.

In the [dimeRocker Unity client](http://dimerocker.com/developers), of which I'm a developer, coroutines are used to send information to and from the servers. Conveniently, coroutines can execute in parallel with your own code or they can be called from another coroutine in order to wait for their completion. Such functionality is useful in Unity for a number of purposes, and seasoned developers will certainly be familiar with them.

{% highlight csharp %}
IEnumerator Start () {
	// Wait for user information to be retrieved
	yield return StartCoroutine(drClient.User.FetchUser());
	// Download friends' profiles without waiting
	StartCoroutine(FetchAllFriends());
}
{% endhighlight %}


In the code above, the first coroutine finishes execution before the second one starts. An easily made mistake though is to call a coroutine without using `StartCoroutine`, as you would a regular method. In this scenario, the coroutine instructions aren't executed and no errors are thrown. Luckily there's a way to prevent such a ghastly mistake. Let's say I have the following coroutine.

{% highlight csharp %}
IEnumerator FetchSomeInfoCoroutine () {
	...
}
{% endhighlight %}

Tantalizing, I know. If I add an additional function that returns a `Coroutine` object...

{% highlight csharp %}
public Coroutine FetchSomeInfo () {
	return StartCoroutine(FetchSomeInfo());
}
{% endhighlight %}

I can now execute the contents of the coroutine simply by calling the public `FetchSomeInfo` method. I don't even have to be aware that I'm executing a coroutine. If I wish to wait for the instructions to complete, I can still pair the method with a `yield` statement.

{% highlight csharp %}
IEnumerator Start () {
	// Execute contents of coroutine
	FetchSomeInfo();
	// Execute contents of coroutine and wait for it to finish
	yield return FetchSomeInfo();
}
{% endhighlight %}

As you can see, eliminating the need for `StartCoroutine` makes the code cleaner and more bulletproof (I myself have made the mistake of calling a coroutine directly, to great frustration). Of course, there is a downside to this method of calling coroutines, which is the reason why the dimeRocker Unity client still requires, for the most part, the use of `StartCoroutine`: developers currently calling coroutines are familiar with using `StartCoroutine`, and sending it a method that returns a `Coroutine` object will cause the compiler to throw an error. But, hopefully developers working on libraries to be used with Unity will adapt this system and folks will get used to it, and we can all have the elegant, "there's no way you can screw this up" code we desire. I'm optimistic.
