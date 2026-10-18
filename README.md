
# Shifting Moral-Ethical Reasoning in LLMs via Prompt Engineering and LoRA Fine-Tuning

Can we shift the actions and reasoning an LLM makes when it is put in a moral dilemma?

This project tests whether a small LLM (Phi-4-mini-instruct) can be steered to consistently reason according to a single ethical framework, in this experiment that was act utilitarianism, when facing difficult moral dilemmas. I compared two approaches: telling the model what it believes through a persona prompt, and training those beliefs into its weights through LoRA fine-tuning on a synthetic dataset I built with Claude Sonnet 4.5. All three variants (base, persona-prompted, fine-tuned) were scored on held-out dilemmas by an LLM judge.

**Key findings**
- Persona prompting won, contrary to my hypothesis: it produced the strongest shift toward act utilitarian reasoning, outscoring the base model on 19 of 20 dilemmas.
- Fine-tuning also worked, zero-shot. With no instructions at inference time, it outscored the base model on 16 of 20 dilemmas and gave noticeably more concise, direct answers.
- The base model often refused or avoided taking a position, while both steered variants always committed to an answer.

[Full paper](shifting_ethical_reasoning_paper.pdf) · [Slide summary](slide_deck_summary.pdf) · [Notebook](shifting_ethical_reasoning_notebook.ipynb)

*Self-directed final project for EN.705.743 at Johns Hopkins University (Fall 2025). Run on Google Colab (A100). To rerun the evaluation, add your OpenAI key to `open_ai_config.json`; never commit real keys.*

## Running the Notebook

- Developed on **Google Colab** (A100 GPU) with Google Drive for storage; much of the code assumes this setup.
- Update the paths in the **"Notebook Variables"** cell near the top of the notebook to match your environment.
- The LLM-judge evaluation uses the OpenAI API. Add your key to `open_ai_config.json` (never commit a real key). A Hugging Face token is also needed where indicated in the notebook.
- **Data:** train and test sets are in `705.743-Ethical_data/`.
- **Results:** model responses are in `outputs/`, and judge scores are in `outputs/evaluations/`.
- **Troubleshooting:** depending on your environment, you may need extra `pip install`s. For example, if the tables in the hyperparameter section don't display, run `pip install ipywidgets`.
