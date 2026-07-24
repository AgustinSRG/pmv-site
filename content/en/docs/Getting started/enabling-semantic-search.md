---
title: Enabling semantic search
description: >
  Guide on how to enable semantic search on PersonalMediaVault
categories: [Guides, Installation, Semantic Search]
tags: [guides, installation, semantic-search]
---

This document is a guide on how to enable semantic search for PersonalMediaVault.

In order to enable semantic search for a vault, you need to perform 2 extra steps:

 - Download an OpenClip embeddings models
 - Enable semantic search by providing the path to the model

## Download OpenClip embedding model

The OpenClip model is required in order to transform text and images into a single representation.

PersonalMediaVault needs a model compatible with [OpenClip](https://github.com/mlfoundations/open_clip) and [ONNX](https://onnx.ai/).

We offer some models as zip files:

| Model | Size | Accuracy | Performance on CPU | Download |
| --- | --- | --- | --- | --- |
| `MobileCLIP2-S2-OpenCLIP-ONNX` | 405 MB | 77.2% | Fast (~70ms) | [Mega](https://mega.nz/file/kSMmxTia#iw5l3w-bwazDAtLiVd03UM-Z-PABoqGzoIfHFmbh-zI) |
| `MobileCLIP2-S3-OpenCLIP-ONNX` | 1 GB | 80.7% | Fast (~110ms) |  [Mega](https://mega.nz/file/dDkWEY6T#S5Yslau5yge7wUXTUaSOM2YQnDW_eaGt3OLWzKyuRVo) |
| `ViT-SO400M-16-SigLIP2-384-ONNX` | 4.6 GB | 84.1% | Slow (~1000ms), GPU recommended | [Mega](https://mega.nz/file/sHMk0LbL#4pimV1VhI4cfn0xjcrdYsjKi7Ns-HIWPvScBMYROogA) |

### Other models

You can find more models in HuggingFace: https://huggingface.co/models?pipeline_tag=zero-shot-image-classification&library=onnx&other=clip

If you are wondering how to download the models from HuggingFace, you can use the hugging face CLI (hf) to download a model, example:

```sh
hf download --local-dir ./MobileCLIP2-S2-OpenCLIP-ONNX RuteNL/MobileCLIP2-S2-OpenCLIP-ONNX
```

Check this guide for more information: https://huggingface.co/docs/hub/main/en/models-downloading#using-the-hugging-face-client-library

You can also transform other OpenClip models in order to turn them into ONNX-compatible format. check this repository for more information: https://github.com/RuurdBijlsma/open-clip-inference-rs#other-models

## Configuring semantic search

### Using Docker

If you are using Docker, check the `.env` file and edit the necessary environment variables.

```conf
# Enable semantic search?
# This option can be YES or NO
# If set to YES, make sure to also set the model
SEMANTIC_SEARCH_ENABLED=NO

# OpenCLIP model path
# First, download a model (you can find models in Hugging face)
# Hugging face search link: https://huggingface.co/models?pipeline_tag=zero-shot-image-classification&library=onnx&other=clip
# Change this variable to point to the model folder
SSE_MODEL_PATH=./open-clip-model

# Max size for images before they cannot be longer encoded
# The size is set in MegaBytes (no decimals allowed)
# This limits the memory usage of the daemon
# If you plan to work with very large images, make sure to set this to a high value
SSE_IMAGE_SIZE_LIMIT_MB=20
```

### Using the launcher

If you are running PersonalMediaVault with the launcher, go to **Configuration** -> **Semantic Search**, enable the semantic search toggle and select the folder where you downloaded the model.

![Screenshot]({{< baseurl >}}images/en/sse-launcher-config.jpg)
