# aitextgen

A robust tool for advanced AI text generation.

aitextgen is a Python package that leverages [Huggingface Transformers](https://github.com/huggingface/transformers) and [pytorch-lightning](https://github.com/PyTorchLightning/pytorch-lightning) with specific optimizations for text generation, plus _many_ added features. It is the successor to textgenrnn and gpt-2-simple, merging the advantages of both packages.

- Finetunes on a pretrained GPT-2 model...or create your own GPT-2 architecture and train from scratch!
- Generates text faster than gpt-2-simple and with better memory efficiency.
- Model agnostic and future-proofed to support new developments in the Transformers-based world.
- With Transformers, aitextgen preserves compatibility with the base package, allowing you to use the model for other NLP tasks and upload to to the Huggingface model repository. Uses the `generate()` function to allow a massive amount of control over the generated text.
- With pytorch-lightning, aitextgen trains models not just on CPU and GPUs, but also _multiple_ GPUs and TPUs! Robust training progress support, with the ability to add optional loggers.
- The input dataset is its own object, allowing you to not only easily encode, cache, and compress them on a local computer before transporting it, but you are able to _merge_ datasets without biasing the resulting dataset, or _cross-train_ models so it learns some data fully and some partially to create blended output.

## Installation

## Usage

## Helpful Notes

- To convert a GPT-2 model trained using earlier TensorFlow-based finetuning tools such as gpt-2-simple to PyTorch, use the transformers-cli command and the [instructions here](https://huggingface.co/transformers/converting_tensorflow_models.html) to convert the checkpoint (where `OPENAI_GPT2_CHECKPOINT_PATH` is the _folder_ containing the model)
- When running on Google Cloud Platform (including Google Colab), it's recommended to download the TF-based GPT-2 from the Google API vs. downloading the PyTorch GPT-2 from Huggingface as the download will be _much_ faster and also saves Huggingface some bandwidth.
- If you want to generate text from a GPU, you must manually move the model to the GPU (it will not be done automatically to save GPU VRAM for training). Either call `to_gpu=True` when loading the model or call `to_gpu()` on the aitextgen object.

## Upcoming Features

The next versions of aitextgen (and one of the reasons I made this package in the first place) will have native support for _schema-based generation_. (see [this repo](https://github.com/minimaxir/gpt-2-keyword-generation) for a rough proof-of-concept)

Additionally, I plan to develop an aitextgen [SaaS](https://en.wikipedia.org/wiki/Software_as_a_service) to allow anyone to run aitextgen in the cloud and build APIs/Twitter+Slack+Discord bots with just a few clicks. (the primary constraint is compute cost; if any venture capitalists are interested in funding the development of such a service, let me know)

I've listed more tenative features in the [UPCOMING](UPCOMING.md) document.

## Maintainer/Creator

Max Woolf ([@minimaxir](https://minimaxir.com))

_Max's open-source projects are supported by his [Patreon](https://www.patreon.com/minimaxir) and [GitHub Sponsors](https://github.com/sponsors/minimaxir). If you found this project helpful, any monetary contributions to the Patreon are appreciated and will be put to good creative use._

## License

MIT

Code from Transformers is used following its Apache License 2.0, with state changes noted when relevant.
