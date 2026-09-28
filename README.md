# Turiya

**A compact AI agent research platform built to measure intelligence per completed task.**

Turiya combines an original causal text architecture with a local harness for memory, retrieval, declarative skills, web lookup, and bounded tool use. A separate conditional stochastic controller explores whether finite-time dynamics can improve action decisions under a strict compute budget. This is an experiment with explicit baselines, not a claim of frontier-model equivalence.

## Current release

- Original **4,074,522,624-parameter** architecture specification and training scaffold.
- Downloadable **5,710,080-parameter tiny checkpoint** trained for two updates on synthetic examples to validate the pipeline.
- Tool harness with local persistence, document retrieval, optional read-only Git, and optional specialist tool routing.
- Evaluation plan that measures task success, memory, latency, tool calls, and energy with matched control systems.

**The tiny checkpoint has no practical assistant capability. Trained 4B weights are not available yet.** An 8 GB Mac is the eventual inference target; it has not been benchmarked with a trained Turiya 4B model.

## Architecture at a glance

The proposed 4B model has 36 gated feed-forward layers, 27 causal convolution state-mixing layers, and nine grouped-query attention layers with tied embeddings. A trained text model would propose answers and tool actions; the host harness controls access to external systems. The stochastic controller is a separately evaluated decision component inspired by [generative thermodynamic computing](https://arxiv.org/abs/2506.15121). Digital simulation does not inherit the paper's projected analog heat savings.

## Try the engineering checkpoint

The 5.71M engineering checkpoint and loader are packaged for a Hugging Face release; **the model repository is pending publication**. With `torch`, `safetensors`, and `tokenizers` installed, `python load_smoke.py` in that package checks loading and a structural forward pass. It is not a chat demo.

## Project status and roadmap

1. Verify architecture, tokenization, training resume and export on a tiny configuration. **Completed for synthetic examples.**
2. Curate rights-reviewed text and tool data; train and evaluate a capable base model. **Pending.**
3. Quantize and measure peak unified memory and latency on an 8 GB Apple Silicon Mac. **Pending.**
4. Compare a tool-equipped baseline, deterministic controller, and stochastic controller on the same held-out tasks. **Pending.**

The site source is in `docs/`. Deployment target: GitHub Pages from the repository's `/docs` folder. The downloadable checkpoint belongs on Hugging Face; no binary weights are checked into this Git repository.

## Reproducibility

The full design constraints and smoke-test details are recorded in `TURIYA_CUSTOM_BUILD.md`; the evaluation protocol is in `eval_protocol.md`. The code is a research scaffold and does not include a trained 4B checkpoint. No license has been assigned to this prepared release yet.
