This is a quick patch (no node, just a monkey patch), but it goes into your comfyui custom_nodes folder.

It solves the problem caused by MeshGraphormer-DepthMapPreprocessor 
(used in repos like https://github.com/Fannovel16/comfyui_controlnet_aux )
that use functions removed from later versions of transformers.

Can't recall where I got it, or I'd credit the person who wrote it, but it works well.
