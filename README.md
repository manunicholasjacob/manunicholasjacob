<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/manunicholasjacob/manunicholasjacob/main/assets/banner-dark.png?v=2">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/manunicholasjacob/manunicholasjacob/main/assets/banner-light.png?v=2">
  <img alt="Manu Nicholas Jacob. Edge AI, computer architecture, LLM inference." src="https://raw.githubusercontent.com/manunicholasjacob/manunicholasjacob/main/assets/banner-light.png?v=2">
</picture>

I measure where the bottleneck actually is, on hardware I can put an ammeter on, and I publish the data whether or not it agrees with me.

[Website](https://manunicholasjacob.com/) · [ORCID](https://orcid.org/0009-0007-6589-6572) · [Google Scholar](https://scholar.google.com/citations?user=inrrUQIAAAAJ&hl=en)

Electrical and computer engineer (UMass Amherst), based in Austin. Hardware engineer at Dell by day, on enterprise AI-server platforms, GPU and PCIe subsystems, and root-cause work. The research below is my own, run on my own hardware.

---

## Tools

**[llama-roofline](https://github.com/manunicholasjacob/llama-roofline)** · [`zenodo.21842493`](https://doi.org/10.5281/zenodo.21842493)<br>
Is your `llama.cpp` decode memory-bandwidth-bound? Measure it in one command. Prints the operating point beside every fitted bandwidth, and refuses to quote a number for silicon it has not measured.

**[ml-systems-lab](https://github.com/manunicholasjacob/ml-systems-lab)** · [`zenodo.21867055`](https://doi.org/10.5281/zenodo.21867055)<br>
One YAML config drives `llama.cpp` and ONNX Runtime sweeps across laptops, a Raspberry Pi over SSH, and GPUs. TTFT, throughput, and per-rail energy from the same run.

**[qgemv-roofline](https://github.com/manunicholasjacob/qgemv-roofline)** · [`zenodo.22164007`](https://doi.org/10.5281/zenodo.22164007)<br>
Twelve CUDA kernels and a Triton implementation of the batch-1 decode GEMV over ggml `q8_0` and `q4_0`, scored against a bandwidth ceiling the harness measures on the same device rather than reads off a spec sheet. Five NVIDIA GPUs, sm_60 through sm_89.

## Measurement studies

Each one ships its data, its harness, and a DOI.

**[The memory wall at the edge of language](https://github.com/manunicholasjacob/edge-llm-memory-wall)** · [`zenodo.21844855`](https://doi.org/10.5281/zenodo.21844855)<br>
Edge LLM decode is bandwidth-bound at R² = 0.994, and the KV cache hits a capacity wall well before compute does.

**[The break-even parallel speedup](https://github.com/manunicholasjacob/edge-breakeven-speedup)** · [`zenodo.21987261`](https://doi.org/10.5281/zenodo.21987261)<br>
Multithreading saves energy exactly when parallel speedup beats the power ratio. Across 831 PMIC-measured runs the power ratio is a board constant and the speedup is a model property, which is what makes the rule usable.

**[Your quantization format is not free](https://github.com/manunicholasjacob/edge-format-tax)** · [`zenodo.21938812`](https://doi.org/10.5281/zenodo.21938812)<br>
Same size, same label, different speed. Provenance changes the layout inside a GGUF file, and format rankings do not transfer between cores.

**[The cold-start tax](https://github.com/manunicholasjacob/edge-cold-start-tax)** · [`zenodo.21844857`](https://doi.org/10.5281/zenodo.21844857)<br>
What a duty-cycled wake actually costs, and the eviction cliff sitting behind it.

**[gguf-faultscope](https://github.com/manunicholasjacob/gguf-faultscope)** · [`zenodo.22163327`](https://doi.org/10.5281/zenodo.22163327)<br>
What one flipped bit does to a quantized model, and where in the file it has to land before anything downstream notices.

---

## Upstream

**[NVIDIA/garak](https://github.com/NVIDIA/garak)** · three merged<br>
A `config_root` fix in `goodside.RileyIsnt`, an ASCII-selection guard in `badchars`, and a restored unreachable-error path in `load_plugin`. The first shipped in garak v0.16.0.

**[ai-dynamo/aiperf](https://github.com/ai-dynamo/aiperf)** · open<br>
Making `crick` optional so `pip install aiperf` needs no C toolchain on aarch64, and a host-telemetry collector category with a RAPL backend, because a CPU-only run currently reports no energy at all. Two of the open PRs are defects in their own tree, found by building against the code rather than reading it.

**[ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)** and **[vllm-project/vllm](https://github.com/vllm-project/vllm)** · issues<br>
Measurement-backed bug reports, including an effective-bandwidth characterisation of Arm decode. Engineers with different hardware have reproduced several of them in-thread, on a 5090 and on server parts.

**[Journal of Open Source Software](https://joss.theoj.org/)** · reviewer<br>
Reviewing submissions, which so far has meant finding a sign error in a published MALA sampler and five merged fixes to the package under review.

---

When a result does not survive re-checking I retract it in public and say why, which is why [one of these repositories](https://github.com/manunicholasjacob/rpi5-quantization-benchmark) opens by withdrawing its own headline.
