---
layout: post
title: Dynamically Loading XML in Flex
---

> <p>XML? Ha! I once wrote some XML! Hilarious!</p>
> <small>Juan Jos&eacute; P&eacute;rez Hern&aacute;ndez</small>

This winter I built a basic video player for a website using Adobe Flex. Beside the viewer was a list of thumbnail images, one for each video. When clicked on these would load the appropriate video and display relevant information below the viewer. This information, as well as the paths to the videos and thumbnail images, was stored in an external XML file. The player worked well, perhaps even excellent, until some of the information in the XML file was changed. The video player still worked, but the new information was nowhere to be found. Below is the tag I used to load the XML data.

{% highlight xml %}
<mx:XML id="vidXML" source="videos.xml" format="e4x" />
{% endhighlight %}

To my surprise, using this tag causes the XML data to be compiled into the .swf rather than loaded at runtime. Making a change to videos.xml didn't do a thing --- indeed, it wasn't even necessary that the XML file exist after compilation.

Now, this is not the behaviour I desired. I wanted to allow others to modify the contents of the XML file and have their changes reflected in the SWF. The solution was to not use the Flex XML tag at all, but rather to use the following code.

{% highlight xml %}
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml" creationComplete="xmlReq.send();">
<mx:HTTPService id="xmlReq" url="videos.xml" resultFormat="e4x" result="toXMLFormat(event)" />

<mx:Script>
<![CDATA[
	import mx.rpc.events.ResultEvent;

	private var vidXML:XML;

	private function toXMLFormat(event:ResultEvent):void {
		vidXML = event.result as XML;
	}
]]>
</mx:Script>
</mx:Application>
{% endhighlight %}

I'm relatively new to the Flex game, so this may seem obvious to veterans in the field, but for new Flexers (Flexies? Flexettes?) it's perhaps something to take note of. I sure wish I had.

Sigh.

