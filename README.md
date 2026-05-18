## AI-Supported Systematic Literature Review Pilot

This repository benchmarks multiple LLMs for screening papers in a systematic review workflow.

Current notebooks:
- `chatgpt-4o.ipynb`
- `claude-3-5.ipynb`
- `gemini.ipynb`
- `mistral.ipynb`
- `deepseek.ipynb`

Each notebook:
1. Loads a screening prompt (`v1_balanced-prompt*.txt`)
2. Loads an input dataset (`correct-abstracts-*.xlsx`)
3. Calls one model provider
4. Writes row-wise predictions to `results/<provider>/...`
5. Reports basic screening metrics (TP/TN/FP/FN, runtime, and where implemented, token cost)

## Repository Layout

- `results/` — model outputs and summaries
- `correct-abstracts-1.xlsx`, `correct-abstracts-500.xlsx` — input datasets
- `v1_balanced-prompt.txt`, `v1_balanced-prompt-without-examples.txt` — prompt variants
- `pyproject.toml` — Python dependencies

## Setup

Requirements:
- Python 3.11+
- Poetry

Install dependencies:

```bash
poetry install
```

Run notebooks with:

```bash
poetry run jupyter lab
```

## Environment Variables

Set provider credentials before running notebooks:

- `OPENAI_API_KEY` (OpenAI notebook; DeepSeek if using OpenAI-compatible client is separate below)
- `DEEPSEEK_API_KEY` (DeepSeek notebook)
- `ANTHROPIC_API_KEY` (Claude notebook)
- `MISTRAL_API_KEY` (Mistral notebook)
- `GOOGLE_CLOUD_PROJECT` + authenticated Google Cloud/Vertex setup (Gemini notebook)

## Notes

- Notebooks are configured to use root-level datasets/prompts and write to `results/`.
- Saved notebook outputs are cleared to keep the repo lighter and avoid stale run artifacts.

## License

- Code and notebooks: [MIT](./LICENSE)
- Datasets, prompts, and benchmark outputs: [CC BY 4.0](./DATA_LICENSE.md)
