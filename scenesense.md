---
# Doncey Albibn
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "SceneSense:"
title_follow: "Diffusion models for 3D Occupancy Synthesis from Partial Observation"
university_name: "University of Colorado - Boulder" # You can comment this out if you dont like it.

author1: "Alec Reed"
author2: "Brendan Crowe"
author3: "Doncey Albin"
author4: "Lorin Achey"
author5: "Bradley Hayes"
author6: "Chris Heckman"

# Links at bottom. Removing '<linkname>_link' below will remove from page.
github_link: "https://github.com/arpg/SceneSense"
github_link_color: "yellowgreen"
github_link_text: "Code"

arxiv_link: "https://arxiv.org/abs/2403.11985"
arxiv_link_color: "blue"
arxiv_link_text: "ArXiv"

# summary_video_link:
# summary_video_link_color:
# summary_video_link_text: "Summary Video Link"

# talk_link: "https://google.com"
# talk_link_color: "red"
# talk_link_text: "IROS Talk"

# media_coverage_link:
# media_coverage_link_color:
# media_coverage_link_text: "Media Coverage"

# bibtex_link: "https://google.com"
# bibtex_link_color: "purple"
# bibtex_link_text: "BiTex"
---

<!-- This is the js script that generates random points on page borders (trying to make a visual nod to diffusion) -->
<script>
    // Gen a rand int bw min and max (inclusive)
    function getRandomInt(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
    }

    // Gen rand color
    function getRandomColor() {
        return '#' + Math.floor(Math.random()*16777215).toString(16);
    }

    // Draw circle at a random pos with rand diam within border
    function drawRandomCircle() {
        var circle = document.createElement('div');
        circle.style.position = 'fixed';
        circle.style.width = 20 * Math.random() + 'px';
        circle.style.height = circle.style.width;
        circle.style.borderRadius = '100%';
        circle.style.backgroundColor = getRandomColor();

        if (Math.random() < 0.5) {
            var x = getRandomInt(0.9*window.innerWidth, window.innerWidth)
            var y = getRandomInt(0, window.innerHeight)
        } else {
            var x = getRandomInt(0, 0.1*window.innerWidth)
            var y = getRandomInt(0, window.innerHeight)
        }

        circle.style.left = x + 'px';
        circle.style.top = y + 'px';

        document.body.appendChild(circle);
    }

    // Using the function above, draw 25 random circles along borders of page
    for (var i = 0; i < 25; i++) {
        drawRandomCircle();
    }
</script>

<div style="text-align: center;">
    We present <b>SceneSense</b>, a novel generative 3D diffusion model for synthesizing 3D occupancy information from observations. SceneSense uses a running occupancy map and a single RGB-D camera to generate predicted geometry around the platform, even when the geometry is occluded or out of view. The architecture of our framework ensures that the generative model never overwrites observed free or occupied space, making SceneSense a low risk addition to any robotic planning stack.
</div>

<br>

<div style="overflow: auto; text-align: center; width: 80%; margin: 0 auto;">
    <img src="/img/scenesense/example_results_h1.png" alt="Photo example results" style="display: inline-block; margin-right: 10px; width: 40%;" height="600">
    <img src="/img/scenesense/example_results_h2.png" alt="Photo example results" style="display: inline-block; margin-left: 10px; width: 40%;" height="600">
</div>

<br>

## Method

Our occupancy in-painting method ensures that observed space remains intact while integrating SceneSense predictions. Drawing inspiration from image inpainting techniques like image diffusion and guided image synthesis, our approach continuously incorporates known occupancy information during inference. To execute occupancy in-painting, we select a portion of the occupancy map for diffusion, generating masks for occupied and unoccupied voxels. These masks guide the diffusion process to modify only relevant voxels while introducing noise at each step. This iterative process, depicted below, enhances scene predictions' accuracy while preventing the model from altering observed geometry.

<div style="overflow: auto; text-align: center;">
    <img src="/img/scenesense/framework.png" alt="SceneSense Framework" style="margin-right: auto; margin-left: auto;" height="500">
</div>

<br>

## Presentation Video

<div style="text-align:center;">
  <video width="80%" controls>
    <source src="/video/scenesense/iros_video.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

<br>

## Citation

```bib
@misc{reed2024scenesense,
      title={SceneSense: Diffusion Models for 3D Occupancy Synthesis from Partial Observation}, 
      author={Alec Reed and Brendan Crowe and Doncey Albin and Lorin Achey and Bradley Hayes and Christoffer Heckman},
      year={2024},
      eprint={2403.11985},
      archivePrefix={arXiv},
      primaryClass={cs.RO}
}
```

<!-- For styling above Bibtex -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.19.0/themes/prism-okaidia.min.css"
      integrity="sha512-pGi87NmT0VeSbmZBK40y3wF4H2DlpCYc5lrO/3F/RPhnwn262NReW3jFtG2iZWhbpoWT5MDzBzawpOri+jcUTw==" crossorigin="anonymous" />

<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.19.0/prism.min.js"
        integrity="sha512-9ndS8HgVHWQq2A/kpIxygbIZQ7oljc9/AvoEv8SQDy192nAuCGSdk7OdAfCZLDkbRJLZMsrV0NXycMSLLNTWCw==" crossorigin="anonymous">
</script>

<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.19.0/plugins/autolinker/prism-autolinker.min.js"
        integrity="sha512-/uypNVmpEQdCQLYz3mq7J2HPBpHkkg23FV4i7/WSUyEuTJrWJ2uZ3gXx1IBPUyB3qbIAY+AODbanXLkIar0NBQ==" crossorigin="anonymous">
</script>

<script src="https://cdn.jsdelivr.net/npm/prismjs-bibtex@2.1.0/prism-bibtex.js"
        integrity="sha256-A5GMUmGHpY8mVpfcaRLQFeHtmdjZLumKBOMpf81FXX0="
        crossorigin="anonymous" referrerpolicy="no-referrer">
</script>