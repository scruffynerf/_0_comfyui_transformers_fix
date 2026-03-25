This is a quick patch (no node, just a monkey patch), but it goes into your comfyui custom_nodes folder.
To install just git clone this repo into your custom_nodes directory,
the _0 in the repo name should ensure it runs early in the node load order.

It solves the problem caused by MeshGraphormer-DepthMapPreprocessor 
(used in repos like https://github.com/Fannovel16/comfyui_controlnet_aux )
that use functions removed from later versions of transformers.

Found the original code here (kudos to them!):
https://github.com/Fannovel16/comfyui_controlnet_aux/issues/578

```Here is a non-destructive Runtime Patch (workaround) that fixes the ImportError: 
cannot import name 'prune_linear_layer' (and the subsequent prune_layer crash) 
without needing to downgrade transformers or modify the core files in comfyui_controlnet_aux.
```

Error looks like this:

`ImportError: cannot import name 'prune_linear_layer' from 'custom_mesh_graphormer.modeling.bert.modeling_utils'`

This method creates a small custom node that loads before ControlNet Aux and injects the missing compatibility functions directly into transformers.modeling_utils in memory.


