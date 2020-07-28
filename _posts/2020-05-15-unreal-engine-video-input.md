---
title: "Unreal Engine Video Input"
---

Lately I've been hacking together a virtual production / realtime filmmaking setup. Think the [mind-blowing work](https://www.youtube.com/watch?v=gUnxzVOs3rk) that Industrial Light & Magic did on *The Mandelorian*, but in my apartment and at a fraction of the quality and without the wonderfully deep pockets of Big Daddy Disney.

In particular, I'm using Unreal Engine to composite a real-life subject into a CGI world in realtime. Camera tracking synchronizes the position of the physical camera with a virtual one. Instead of ILM's fancy video wall, a humble green screen. Sometimes this technique is called "mixed reality", though usually you hear that term in the context of capturing virtual reality experiences.<sup><a href="#fn1" id="r1">[1]</a></sup>

The first step: get a live video feed into Unreal. Fortunately Epic Games has been going hard on the pro video I/O front and has made this straightforward with the right hardware.


## Capture Card

With that said, the officially [supported](https://docs.unrealengine.com/en-US/Engine/ProVideoIO/BlackmagicIOReference/index.html) [options](https://docs.unrealengine.com/en-US/Engine/ProVideoIO/AJAIOReference/index.html) are disheartening for the price conscious.
Unreal supports capture cards from Blackmagic Design and AJA, but the cheapest one on their list with HDMI support is the DeckLink 4K Extreme 12G which costs a cool USD $895. That's a lot of Benjamins.

I opted instead for the BMD [DeckLink Mini
Recorder](https://www.blackmagicdesign.com/products/decklink/techspecs/W-DLK-06). It's not officially supported, so it was a gamble.

<img alt="DeckLink Mini Recorder box" srcset="/images/decklink-mini-recorder-box.jpg 1x, /images/decklink-mini-recorder-box@2x.jpg 2x" src="/images/decklink-mini-recorder-box.jpg">

<img alt="DeckLink Mini Recorder card" srcset="/images/decklink-mini-recorder-card.jpg 1x, /images/decklink-mini-recorder-card@2x.jpg 2x" src="/images/decklink-mini-recorder-card.jpg">

Fortunately it works a treat. Install the PCIe card, download some software, configure Unreal, and Bob's your uncle.<sup><a href="#fn2" id="r2">[2]</a></sup>

<video controls src="/videos/unreal-video-input.mp4"></video>


## Alternatives

The BMD [UltraStudio Mini Recorder](https://www.blackmagicdesign.com/products/ultrastudio/techspecs/W-DLUS-04) --- basically the Thunderbolt version of the DeckLink --- was tempting for its ability to plug into my laptop. Unfortunately my desktop lacks Thunderbolt so I skipped that option.

The BMD [Intensity](https://www.blackmagicdesign.com/products/intensitypro4k/techspecs/W-INT-05) seems to be a popular option for capturing HDMI and has the bonus of HDMI output. Recording and monitoring in one card, what's not to love? Alas, [forum](https://forums.unrealengine.com/unreal-engine/feedback-for-epic/1655497-hdmi-video-capture-card-support-for-virtual-production) [posts](https://forums.unrealengine.com/community/general-discussion/1646571-video-capture-cards-not-working-supported-help) indicate that Unreal refuses to recognize it. So that's not to love.

Another attractive option was the Elgato [Cam Link](https://www.elgato.com/en/gaming/cam-link-4k), which converts any HDMI source to a webcam feed. It's relatively cheap and the Internet tells me it works well with Unreal. I might have went this route if it didn't prove impossible to find. I'll chalk this up to COVID-19 and the sudden surge of people decking out their work-from-home setups.

Yet another Elgato doodad that looked promising was the [Game Capture HD60
S](https://www.elgato.com/en/gaming/game-capture-hd60-s). Reports indicate that it too works with Unreal. Might be a good option, but alas, also nowhere to be found.


## HDMI Output Woes

One unexpected obstacle was that my DLSR, a Canon 60D, lacks clean HDMI output. You can get a live feed, but with overlays. No bueno. For now my GoPro suffices, but it's hardly the ideal studio camera. Time to upgrade.


---

<ol class="footnotes">
    <li id="fn1">Need to capture a VR playthrough? Consider <a href="https://mixcast.me">MixCast</a>, which I helped develop when I worked at Blueprint Reality.<a href="#r1" class="return"></a></li>
    <li id="fn2">Or in my case, Charles, Dave, Don, Jack, Lee, Sanford, and Tom.<a href="#r2" class="return"></a></li>
</ol>
