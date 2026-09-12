# Experimental GGUF branch status

This branch adds local checkpoint selection, qwen4exp and qwen35moe text adapters,
and direct packed GGUF execution through custom MLX Metal kernels. Selected
experts execute in bounded batches, with packed-buffer caching and float32
activations and accumulation. Dependency pins and named safetensors tiers are
unchanged.

The final regression run passed 162 tests, with one skipped and four slow tests
deselected. Both 512-token prefill plus 128-token generation trials completed;
the process lifetime peak physical footprint was 4.65 GiB. See
[validation results](benchmarks/gguf-packed-m5.json) and [usage](gguf.md).

This remains a prototype for discussion. Matched decoded-path performance
comparisons, compiler timing, and broader real-checkpoint numerical validation
remain unfinished. The separate PR message is being reviewed locally; no PR has
been opened.
