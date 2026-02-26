# Qwen-Qwen3-4B — CPU optimization

This folder contains Olive recipes for optimizing Qwen-Qwen3-4B targeting the CPU EP.

MMLU evaluation: 0.72 
## What this folder is for

- Execution Provider: CPU EP
- Typical precision: INT4 precision by default
- Example recipe filename: Qwen-Qwen3-4B_cpu_int4_kld_gradient.json

## Setup

1) Install the main branch of Olive:
   - pip install git+https://github.com/microsoft/olive.git
2) Install the required runtime and dataset packages for this backend:
   - onnxruntime-genai (CPU build)
   - datasets
   - transformers==4.52.4
   - accelerate
   - pip install -r requirements.txt
3) Run Olive to build/optimize the model
   - olive run --config Qwen-Qwen3-4B_cpu_int4_kld_gradient.json
4) Run an MMLU eval on the optimized model
   - olive run --config Qwen-Qwen3-4B_cpu_int4_kld_gradient-eval.json

Additional notes:
- Optional: Use best practices when considering accuracy vs. memory to improve throughput on CPU.
- Runs purely on CPU; no GPU required.

---

Eval results log

+------------+-------------------+-------------------------+----------------+--------------------------------------------------------+
| model_id   | parent_model_id   | from_pass               |   duration_sec | metrics                                                |
+============+===================+=========================+================+========================================================+
| d272a4cc   | b59880be          | modelbuilder            |     0.00200009 | {                                                      |
|            |                   |                         |                |   "mmlu-acc": 0.7210526315789474,                      |

