# Contrastive learning and price ordering

Executed simulation notebooks accompanying Hamed Zakeri's report on *Self-Supervised Learning with Data Augmentations Provably Isolates Content from Style* (von Kügelgen et al., NeurIPS 2021).

The report studies the proposed price of a latent quantity,

$$
\pi(q)=\frac{\operatorname{Var}(q(\tilde z)-q(z))}{\operatorname{Var}(q(z))},
$$

and the hypothesis that lower-priced information is preferentially retained. A benchmark proposition proves an ordering under restricted linear–Gaussian assumptions. These notebooks assess recovery under finite InfoNCE training in settings that also depart from those assumptions.

## Notebooks and saved results

The six notebooks below cover the five experiments and the longer-training follow-up within Experiment 2. **The notebooks are preserved exactly as uploaded, including their saved outputs.** Only their filenames have been normalised for this repository. Their original upload names and checksums are recorded in [notebook_manifest.json](notebook_manifest.json).

| Report material | Notebook | Saved run coverage |
| --- | --- | --- |
| Experiment 1 — one spare representation dimension | [01_experiment1_spare_seat_3seeds.ipynb](notebooks/01_experiment1_spare_seat_3seeds.ipynb) | Three seeds; five- and six-output comparisons; completed recovery and forward-fit tables for all seven settings, plus Figure 1 with updated labels. |
| Experiment 2 — perturbing the originally designated content | [02_experiment2_perturbed_content.ipynb](notebooks/02_experiment2_perturbed_content.ipynb) | Three seeds for each invariant/perturbed comparison across the paper's four cases, at 10,000 updates. |
| Experiment 2 — Case 3 longer-training follow-up | [02_experiment2_perturbed_content_longer_training.ipynb](notebooks/02_experiment2_perturbed_content_longer_training.ipynb) | One fixed data-generating setting and three paired training seeds, evaluated at 10,000, 30,000 and 60,000 updates; saved recovery figure with means and sample standard deviations. |
| Experiment 3 — non-Gaussian distributions | [03_experiment3_nongaussian_world.ipynb](notebooks/03_experiment3_nongaussian_world.ipynb) | Three seeds, five and six outputs, 10,000 updates; saved recovery and forward-fit results. |
| Experiment 4 — training budget and price differences | [04_experiment4_finite_budget.ipynb](notebooks/04_experiment4_finite_budget.ipynb) | Three seeds per reported comparison; saved recovery and forward-fit results for every condition and budget. |
| Experiment 5 — invariant functions under reflection versus redraw | [05_experiment5_nonlinear_heads_reflection_gaussian.ipynb](notebooks/05_experiment5_nonlinear_heads_reflection_gaussian.ipynb) | Three seeds at 10,000, 30,000 and 60,000 updates. The report uses the Gaussian reflection/redraw comparison. |

### How to read the saved notebooks

- In Experiment 3, introductory references to one seed, two trainings or cleared outputs are stale. The code and saved outputs show three seeds and six completed runs. Its JSON cache reuses completed results; it does not resume an interrupted optimiser trajectory.
- In Experiment 4, the introductory and metadata notes saying that training has not been executed are stale. Completed three-seed tables, figures and forward-fit results are embedded.
- Experiment 2 also retains an independent single-seed strength sweep and historical tables. The report's four-case results come from the **paired invariant/perturbed comparison**, not the historical tables.
- Experiment 5 also retains exploratory output-head/sigmoid comparisons. Those are outside the final report's Experiment 5 discussion; use the **reflection/redraw augmentation comparison** for that discussion.
- Experiment 1's preparation notes and `prepared_for_user_execution` metadata predate this completed rerun. All 21 neural runs and their forward-fit results are saved; the optional linear toy is skipped by default.

## Viewing and running

Saved tables and figures can be inspected without rerunning training. To rerun a notebook, open it in Jupyter or Google Colab and use its settings and run instructions. The Python dependencies are listed in [requirements.txt](requirements.txt); the saved setup outputs record the environments used for the runs. The dependency list is unpinned and is not an exact environment lockfile.

The notebooks are self-contained adaptations and do not require a local copy of the original repository. Full neural training is substantially more expensive than viewing the saved outputs. Some Run All paths also execute exploratory sections, particularly in Experiment 5.

The notebooks reference local/Colab result directories containing CSVs, JSON results and, in some versions, model checkpoints and encoded arrays. **Those directories are not bundled in this archive.** Existing compatible caches can be reused only if available in the running environment; saved notebook outputs alone do not contain model checkpoints. Fresh execution without those caches may rerun training. Preserve the result directories in persistent storage when running in Colab.

Recovery probes predict latent factors or functions from representations. Forward fits predict representations from latents and assess approximate linearity of the composite map. Probe recovery does not establish global optimality of the trained models.

## Original work

The simulation structure was studied using the paper's released implementation, particularly `main_mlp.py` in [ysharma1126/ssl_identifiability](https://github.com/ysharma1126/ssl_identifiability). The notebooks record the source repository and source commit in their metadata.

Reference: von Kügelgen et al. (2021), *Self-Supervised Learning with Data Augmentations Provably Isolates Content from Style*, NeurIPS.
