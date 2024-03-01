---
# Doncey Albibn
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "SceneSense:"
title_follow: "Diffusion models for 3D Occupancy Synthesis from Partial Observation"
university: "University of Colorado - Boulder"

author1: "Alec Reed"
author2: "Brendan Crowe"
author3: "Doncey Albin"
author4: "Bradley Hayes"
author5: "Chris Heckman"

# Links at bottom. Removing '<linkname>_link' below will remove from page.
github_link: "https://google.com"
github_link_color: "yellowgreen"
github_link_text: "GitHub"

arxiv_link: "https://google.com"
arxiv_link_color: "blue"
arxiv_link_text: "ArXiv"

# summary_video_link:
# summary_video_link_color:
# summary_video_link_text: "Summary Video Link"

talk_link: "https://google.com"
talk_link_color: "red"
talk_link_text: "IROS Talk"

# media_coverage_link:
# media_coverage_link_color:
# media_coverage_link_text: "Media Coverage"

bibtex_link: "https://google.com"
bibtex_link_color: "purple"
bibtex_link_text: "BiTex"
---

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

    // Draw 25 random circles along left or right border of page
    for (var i = 0; i < 25; i++) {
        drawRandomCircle();
    }
</script>


<div style="text-align:center;">
    We present ***SceneSense***, a novel generative 3D diffusion model for synthesizing 3D occupancy information from observations. SceneSense uses a running occupancy map and a single RGB-D camera to generate predicted geometry around the platform, even when the geometry is occluded or out of view. The architecture of our framework ensures that the generative model never overwrites observed free or occupied space, making SceneSense a low risk addition to any robotic planning stack.
</div>

<br>

<div style="overflow: auto;">
    <img src="/img/scenesense/example_results_h2.png" alt="Photo example results" style="float:right; margin-right:100px;margin-left:100px;" height="600">
    <p>
        We present <strong>SceneSense</strong>, a novel generative 3D diffusion model for synthesizing 3D occupancy information from observations. SceneSense uses a running occupancy map and a single RGB-D camera to generate predicted geometry around the platform, even when the geometry is occluded or out of view. The architecture of our framework ensures that the generative model never overwrites observed free or occupied space, making SceneSense a low risk addition to any robotic planning stack.
    </p>
</div>

