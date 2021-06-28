---
title: "Screenshots with Unity Recorder"
---

There's a chance your Unity project contains a script like this to take screenshots:

```csharp
using UnityEditor;
using UnityEngine;

class MyTools
{
    [MenuItem("MyTools/Screenshot")]
    static void Screenshot()
    {
        ScreenCapture.CaptureScreenshot("MyScreenshot");
    }
}
```

If you only need screenshots from the editor, consider Unity's [Recorder](https://docs.unity3d.com/Packages/com.unity.recorder@latest/index.html). You commonly use this package to capture gameplay videos, but it can also save single stills on demand. You can set custom resolutions, target specific cameras, and switch between image formats. You can even wow your friends with 360° panoramas.

1. Install Recorder via the package manager
1. From the Recorder window, add an Image Sequence recorder
1. Set *Recording Mode* to "Single Frame"
1. Uncheck *Exit Play Mode*
1. When you need a screenshot, hit *Start Recording*

<img alt="Unity Recorder configured for screenshot" srcset="/images/unity-recorder-screenshot.png 1x, /images/unity-recorder-screenshot@2x.png 2x" src="/images/unity-recorder-screenshot.png">

It puts `ScreenCapture.CaptureScreenshot` to shame.
