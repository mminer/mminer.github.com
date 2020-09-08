---
title: "Run Sourceless Plugins in a Custom Unreal Build"
---

If you compile Unreal Engine from source and open a project, it might complain that some plugin modules "are missing or built with a difference engine version," despite being built with the same semantic version.

<img alt="Unreal Engine missing modules dialog" src="/images/unreal-missing-modules.png">

If your plugin includes its source, rebuild and carry on friend. But if not --- if it's a binaries-only distribution --- you need to edit a file to make it work.<sup><a href="#fn1" id="r1">[1]</a></sup>

Unreal determines if a plugin is compatible with the engine in [`FModuleManager::IsModuleUpToDate`](https://docs.unrealengine.com/en-US/API/Runtime/Core/Modules/FModuleManager/IsModuleUpToDate/index.html). Step through the code and you see that it does so by comparing the plugin build ID with the engine's.<sup><a href="#fn2" id="r2">[2]</a></sup> Make these build IDs match and your project will open without complaint.

The engine build ID is stored in *Engine/Binaries/Win64/UE4Editor.modules*. This value is 13144385 in Epic's 4.25 build. In a version compiled from source it's a <abbr title="Universally Unique Identifier">UUID</abbr>, e.g. 5f645f3f-d8d1-4fbf-a1e6-866a7c8bb809. A plugin's build ID is likewise stored in *PLUGIN_NAME/Binaries/Win64/UE4Editor.modules*.<sup><a href="#fn3" id="r3">[3]</a></sup>

All you need to do is update the plugin's *UE4Editor.modules* file with the engine build ID. Easy peasy.


---

<ol class="footnotes">
    <li id="fn1">
        This scenario &mdash; building the engine yourself but lacking the source to plugins you use &mdash; is probably rare. <a href="https://www.unrealengine.com/en-US/marketplace-guidelines#262a">Epic&rsquo;s marketplace guidelines</a> require that plugins include their source to avoid this problem.
        <blockquote>Customers should have the plugin source code that's dependent on Unreal Engine source code so that they may attempt to compile it against source-built versions of the engine.<a href="#r1" class="return"></a></blockquote>
    </li>
    <li id="fn2">Here&rsquo;s <a href="https://github.com/EpicGames/UnrealEngine/blob/df84cb430f38ad08ad831f31267d8702b2fefc3e/Engine/Source/Runtime/Core/Private/Modules/ModuleManager.cpp#L1083">the line</a> that compares the build IDs.<a href="#r2" class="return"></a></li>
    <li id="fn3">Replace <em>Win64</em> with the platform you run Unreal on.<a href="#r3" class="return"></a></li>
</ol>
