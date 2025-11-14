# Viewing Registered Multimodal Datasets in Napari

![pastedImage](https://github.com/user-attachments/assets/b3434888-36e9-41a5-8ee5-304e7581b800)

With these you can select both single-channels for the CODEX and single transcripts for the Xenium.
It's not ideal having to copy them to the Napari console, but we could turn them into something more polished later.

napari-spatialdata downsamples point layers by default to 100.000 points, which is too sparse for this use case: https://github.com/scverse/napari-spatialdata/blob/aea2eb559c536aae64ba1a57dc71d26c2c66db28/src/napari_spatialdata/constants/config.py#L2
We can load and view all the transcripts, by overwriting the limit before we load the core into napari, by using the console window and these lines:
```
import napari_spatialdata
napari_spatialdata.constants.config.POINT_THRESHOLD = 10**9 # A billion here is just an example, any large number is fine.
```

## Script to add widgets to Napari for interactive viewing

The scripts require 'napari' with the `napari-spatialdata` plugin (https://spatialdata.scverse.org/projects/napari/en/latest/) installed. 

To use the scripts:
1) Open Napari
2) Load the SpatialData object with `Open with Plugin` - > `OpenFolder` -> `xeniumcodex.zarr`:

  The object contains two coordinate spaces:
  - `codex`: original codex coordinates (you can ignore this)
  - `global`: Xenium + aligned codex data (this should be used for visualization)
  The `global` space should be used for visualization.

![image](https://github.com/user-attachments/assets/2a310578-5850-41d3-9043-be81c2ebf794)

3) Load the `codex` and `transcripts` layers.
   
![image](https://github.com/user-attachments/assets/4611015f-4f26-4871-87c8-888881c154e6)

5) Open the napari consloe with `Window` -> `Console` 
6) Copy-Paste the scripts in the Napari console, this will make the widgets appear on the right side.

### CODEX Channel Selector

`codex_selector.py`

Creates a new image layer from the selected CODEX channel. The colormap and range of the selected channel can then be selected from the standard Napari UI on the top left. 

![image](https://github.com/user-attachments/assets/7b082eb6-bad3-4b88-8b2c-bccfdc7e6c03)

###  Xenium Transcript Selector

`codex_selector.py`

Creates a new point layer from the selected Xenium . After selecting all points with `Ctrl + A`, their size and color can be changed from the standard napari UI.

![image](https://github.com/user-attachments/assets/93c8bb52-68fb-4f84-8af3-07779b7a3bd8)



