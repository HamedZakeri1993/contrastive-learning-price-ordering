# Contrastive learning and price ordering

Executed simulation notebooks accompanying Hamed Zakeri's report on *Self-Supervised Learning with Data Augmentations Provably Isolates Content from Style* ([von Kügelgen et al., NeurIPS 2021](https://arxiv.org/abs/2106.04619)).

The report studies the price of a latent quantity with finite, positive variance,

$$
\pi(q)=\frac{\operatorname{Var}(q(\tilde z)-q(z))}{\operatorname{Var}(q(z))},
$$

and the hypothesis that lower-priced information is preferentially retained. This price equals normalized mean-square change when the change has mean zero. The report's benchmark proposition establishes a subspace ordering under restricted linear–Gaussian assumptions and a fixed-total-variance constraint. The notebooks assess recovery after finite contrastive training, including settings outside that benchmark.

## Notebooks and saved results

The six notebooks cover five experiments and the longer-training follow-up within Experiment 2. Their explanations have been revised to match the implemented designs and saved results. **All code cells, saved outputs, execution counts, cell IDs, and metadata are unchanged.** The original files are preserved in the [timestamped backup](backups/2026-10-30_11-58-12-0400/). Original upload names, current checksums, backup paths, and preservation checks are recorded in [notebook_manifest.json](notebook_manifest.json).

| Report material | Notebook | Saved report-relevant results |
| --- | --- | --- |
| Experiment 1 — one spare representation dimension | [01_experiment1_spare_seat_3seeds.ipynb](notebooks/01_experiment1_spare_seat_3seeds.ipynb) | Seven settings, three seeds, 10,000 updates: 21 runs, recovery and forward-fit tables, and Figure 1. |
| Experiment 2 — perturbing original content | [02_experiment2_perturbed_content.ipynb](notebooks/02_experiment2_perturbed_content.ipynb) | Four settings, two paired content conditions, three seeds, 10,000 updates: 24 main-comparison runs. |
| Experiment 2 — longer training in Case 3 | [02_experiment2_perturbed_content_longer_training.ipynb](notebooks/02_experiment2_perturbed_content_longer_training.ipynb) | One fixed world, three paired training seeds, two conditions: six trajectories evaluated at 10,000, 30,000, and 60,000 updates, plus Figure 2. |
| Experiment 3 — non-Gaussian latent factors | [03_experiment3_nongaussian_world.ipynb](notebooks/03_experiment3_nongaussian_world.ipynb) | Five and six outputs, three seeds, 10,000 updates: six runs with recovery and forward-fit results. |
| Experiment 4 — training budget and price differences | [04_experiment4_finite_budget.ipynb](notebooks/04_experiment4_finite_budget.ipynb) | Eight condition/budget combinations and three seeds: 18 trajectories and 24 evaluations. |
| Experiment 5 — reflection versus independent redraw | [05_experiment5_nonlinear_heads_reflection_gaussian.ipynb](notebooks/05_experiment5_nonlinear_heads_reflection_gaussian.ipynb) | Two augmentation rules, three seeds, and evaluations at 10,000, 30,000, and 60,000 updates: six report-relevant trajectories and 18 evaluations. |

### Scope of the saved material

- Experiment 1's optional linear toy is disabled by default. Its 21 neural runs and forward fits are complete.
- The main Experiment 2 notebook also contains an independent single-seed strength sweep and historical static tables. The report's main comparison uses the paired invariant/perturbed table. The longer-training notebook holds the world fixed, so its seed variation has a different interpretation.
- Experiments 3 and 4 include completed three-seed results. Experiment 3 caches completed scores; Experiment 4 supports resuming training from saved model, optimizer, and random-generator states.
- Experiment 5 also contains an exploratory identity-versus-sigmoid output-head comparison. Including that comparison, the notebook contains 12 trajectories and 36 evaluations; the report discusses the reflection/redraw subset.

Historical preparation labels in code comments and notebook metadata are retained as part of the unchanged execution record. The Markdown explanations describe the saved completed experiments.

## Viewing and running

Open the notebooks on GitHub, in Jupyter, or in Google Colab to inspect their saved tables and figures without rerunning training. For a fresh execution, run the cells in order and follow the settings described in each notebook. [requirements.txt](requirements.txt) lists the Python dependencies; it is unpinned and is not an exact environment lockfile. Saved setup outputs record the versions used for the archived runs.

The notebooks are self-contained adaptations and do not require a local checkout of the original implementation. Full training and probe fitting are substantially more expensive than viewing saved outputs. Run All also executes enabled exploratory sections, especially in Experiment 5.

The external result directories, CSV/JSON caches, model checkpoints, and encoded arrays referenced by the notebooks are **not bundled in this repository**. Existing compatible caches can be reused only when available in the running environment. Saved notebook outputs alone cannot resume training. Keep generated result directories in persistent storage when running in Colab; fresh execution without compatible caches may retrain the models.

Recovery probes predict latent factors or functions from representations. Forward fits predict representations from latents and assess approximate affine structure on the sampled distribution; the linear regression fits include an intercept. High recovery does not prove exact identifiability, and near-zero probe scores do not establish complete absence of information. None of these diagnostics proves global optimality of the trained encoder.

## References and provenance

- von Kügelgen et al. (2021). *Self-Supervised Learning with Data Augmentations Provably Isolates Content from Style*. Advances in Neural Information Processing Systems 34. [Paper](https://arxiv.org/abs/2106.04619).
- [Released simulation implementation](https://github.com/ysharma1126/ssl_identifiability/tree/ee46a35acf68461172b3eaeeb1d6fbc779fce661), particularly `main_mlp.py`, `spaces.py`, and `losses.py`. The notebooks record the upstream repository and commit in their metadata. The price-ordering experiments extend that simulation design.
- [Original notebook snapshot and backup index](backups/2026-10-30_11-58-12-0400/README.md), taken before the Markdown cleanup.
