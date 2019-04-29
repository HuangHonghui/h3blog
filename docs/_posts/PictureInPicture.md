---
title: About Picture In Picture
date: 2019-04-03 14:10:00 +0800
type: post
blog: true
---

# About Picture In Picture(pip)

## Abstract
This specification intends to provide APIs to allow websites to create a floating video window always on top of other windows so that users may continue consuming media while they interact with other content sites, or applications on their device.


pip直接翻译就是画中画，这个Api可以让视频浮与所有的浏览器窗口之上。你可以一边看视频，一边浏览其他的网页。


## 例子
``` js
<video id="video" src="https://example.com/file.mp4"></video>

<button id="togglePipButton"></button>

<script>
  const video = document.getElementById('video');
  const togglePipButton = document.getElementById('togglePipButton');

  // Hide button if Picture-in-Picture is not supported or disabled.
  togglePipButton.hidden = !document.pictureInPictureEnabled ||
    video.disablePictureInPicture;

  togglePipButton.addEventListener('click', function() {
    // If there is no element in Picture-in-Picture yet, let’s request
    // Picture-in-Picture for the video, otherwise leave it.
    if (!document.pictureInPictureElement) {
      video.requestPictureInPicture()
      .catch(error => {
        // Video failed to enter Picture-in-Picture mode.
      });
    } else {
      document.exitPictureInPicture()
      .catch(error => {
        // Video failed to leave Picture-in-Picture mode.
      });
    }
  });
</script>
```
<p class="codepen" data-height="400" data-theme-id="0" data-default-tab="js,result" data-user="MimoHuang" data-slug-hash="vPooGq" style="height: 400px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid black; margin: 1em 0; padding: 1em;" data-pen-title="picture in picture">
  <span>See the Pen <a href="https://codepen.io/MimoHuang/pen/vPooGq/">
  picture in picture</a> by HuangHonghui (<a href="https://codepen.io/MimoHuang">@MimoHuang</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
