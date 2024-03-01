---
type: article
# title: "SceneSense:"
# description: "Diffusion models for 3D Occupancy Synthesis from Partial Observation"
# author_clean: Alec Reed, Brendan Crowe, Doncey Albin, Bradley Hayes, and Chris Heckman
---

<div style="text-align:center; font-size: 36px;">
    <strong>SceneSense:</strong> Diffusion models for 3D Occupancy Synthesis from Partial Observation
</div>

<br>

<div style="text-align: center; background-color: white; color: black; padding: 10px; width: 50wv;">
    <div style="display: inline-block; width: 18%;"><strong>Alec Reed</strong></div>
    <div style="display: inline-block; width: 18%;"><strong>Brendan Crowe</strong></div>
    <div style="display: inline-block; width: 18%;"><strong>Doncey Albin</strong></div>
    <div style="display: inline-block; width: 18%;"><strong>Bradley Hayes</strong></div>
    <div style="display: inline-block; width: 18%;"><strong>Chris Heckman</strong></div>
</div>

--- 

<br>

<script>
    /*
     * Doncey A. 
     * Draw random circles along paper frame borders, kind of like adding noise during diffusion.
     * 
    */

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

