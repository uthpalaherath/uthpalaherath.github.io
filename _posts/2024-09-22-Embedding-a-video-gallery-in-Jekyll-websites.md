---
title: Embedding a video gallery in Jekyll websites
excerpt:
date: 2024-09-22
toc: false
tags:
  - tutorials
  - jekyll
  - minimal-mistakes
  - html
header:
  teaser: /assets/media/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922105246495.png
---
{: .notice--primary}
*A simple tutorial on embedding a video gallery in a Minimal Mistakes themed Jekyll website.*

![2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922105246495](/assets/media/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922105246495.png)

The [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) theme [^1] for Jekyll websites by Michael Rose offers a great way to embed images in a [gallery layout](https://mmistakes.github.io/minimal-mistakes/post%20formats/post-gallery/). I wanted to do the same for videos. In this post I will show you how I achieved that.

First, we create a gallery layout using a custom CSS by adding the following snippet in `assets/css/main.scss`.

```css
.video-gallery {
  display: flex;
  flex-wrap: wrap;
  gap: 20px; /* Space between the videos */
  justify-content: space-between;
}

.video-item {
  flex: 1 1 calc(33.33% - 20px); /* 33.33% width for 3 items per row */
  margin-bottom: 20px; /* Space between rows */
}

.video-item video {
  width: 100%; /* Make videos responsive */
  height: auto;
}
```

Here, we use `flex-wrap:wrap;` to wrap items onto the next line. `flex: 1 1 calc(33.33% - 20px);` ensures that each video takes up one-third of the available space (minus the gap) such that we limit 3 videos per row. You can modify this according to your needs.

Next, in your markdown file you can embed the video gallery using a HTML structure as follows.

```html
<div class="video-gallery">
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/videos/video1.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/videos/video2.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/videos/video3.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <!-- Add more video items as needed -->
</div>
```

Optionally, you may also want to set,

```markdown
toc: false
classes: wide
```

in your YAML front matter to ensure all the available space is being used for the gallery layout.

On some browsers (e.g.- Chrome), `.mov` files aren't rendered correctly so we have to convert them to `.mp4` with the `H.264` codec. I used the [ffmpeg](https://www.ffmpeg.org) [^2] utility to do the conversion as follows,

```shell
ffmpeg -i video1.mov -vcodec h264 -acodec aac video1.mp4
```

To showcase the gallery layout view, I am sharing some videos I captured from a Breaking Benjamin, Staind, Daughtry and Lakeview concert [^3] I attended in Raleigh the other day. Enjoy some of my favorite bands I've been listening to since high school!

<div class="video-gallery">
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/media/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922114125601.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/media/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922114135400.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/media/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922114143925.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/media/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922114151896.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/media/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922114203117.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <div class="video-item">
    <video width="560" height="315" controls>
      <source src="{{ "/assets/media/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites/2024-09-22-Embedding-a-video-gallery-in-Jekyll-websites-20240922114211171.mp4" | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
</div>

# References

[^1]: [https://mmistakes.github.io/minimal-mistakes/](https://mmistakes.github.io/minimal-mistakes/)
[^2]: [https://www.ffmpeg.org](https://www.ffmpeg.org)
[^3]: [https://www.livenationentertainment.com/2024/03/rock-icons-staind-and-breaking-benjamin-announce-co-headline-tour-with-special-guests-daughtry-and-lakeview/](https://www.livenationentertainment.com/2024/03/rock-icons-staind-and-breaking-benjamin-announce-co-headline-tour-with-special-guests-daughtry-and-lakeview/)
