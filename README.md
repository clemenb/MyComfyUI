Hey r/comfyui! I’ve crafted a ComfyUI workflow that batch-processes images to generate captions using **BLIP Analyze Image** and **Florence2Run**, then saves each image with its own .txt caption file using **ImageBatchSaver**—perfect for AI training datasets. Check it out on my site: [makuta.io/comfyui-batch-captioning](https://makuta.io/comfyui-batch-captioning).

**Workflow Breakdown**:
- **LoadImagesFromFolderKJ** (from comfyui-kjnodes): Loads up to 6 images from a folder (e.g., `C:\Users\clement\ComfyUI\output\Character02`).
- **BLIP Analyze Image** (from was-ns): Generates basic captions (48-96 chars, CPU-friendly).
- **Florence2Run** (from comfyui-florence2): Adds detailed captions (task: "more_detailed_caption", fp16/sdpa).
- **PreviewImage** (comfy-core): Visualizes images for quick checks.
- **ImageBatchSaver** (from the ComfyUI-Batch-Process pack [by Zar4X]—it saves images with companion .txt files per image (e.g., Alix_0001.png + Alix_0001.txt).

**Critical Path-Saving Tip**:
- Connecting **LoadImagesFromFolderKJ**’s `image_path` output to **ImageBatchSaver**’s `output_path` input auto-derives filenames from input images and saves to ComfyUI’s default output folder (e.g., `C:\Users\[user]\ComfyUI\output\Character02`). Great for quick tests!
- For a custom folder (e.g., a dedicated training dir), skip the connection and manually enter the full filepath in **ImageBatchSaver**’s `output_path` widget (e.g., `D:\MyDatasets\Character02`). This ensures precise control.

Screenshots: [Embed 3-6 images: workflow canvas, LoadImagesFromFolderKJ-to-ImageBatchSaver connection, sample outputs]

Download the JSON and full setup guide at [makuta.io/comfyui-batch-captioning](https://makuta.io/comfyui-batch-captioning). Install nodes via ComfyUI Manager: search for comfyui-kjnodes, was-ns, comfyui-florence2, batch-process, comfyui-easy-use (for **easy showAnything** previews).

What do you think? Ideas for LoRA or video batching? Join the discussion on my site or share your remixes! [makuta.io/comfyui-batch-captioning](https://makuta.io/comfyui-batch-captioning)

#ComfyUI #StableDiffusion #AICaptions
