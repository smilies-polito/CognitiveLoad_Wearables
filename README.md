# Cognitive Load Wearable Dataset

**📦 Zenodo Dataset:** [Zenodo_CognitiveLoad](https://doi.org/10.5281/zenodo.20815030)

**📄 Associated Article:** Coletta A., Circhetta M., Calderisi S., Di Biase A., Masi G., Ferraris C., and Olmo G. *Wearable Monitoring of Cognitive Load: A Comparative Sensor Study*. Accepted for presentation at the **EAI PervasiveHealth Conference 2026**. DOI and publication details will be added upon release.

---

# Overview

This repository accompanies a study on **multimodal physiological monitoring of cognitive workload** using wearable sensors. While the **complete raw dataset** is hosted on Zenodo, this GitHub repository contains the documentation and code necessary to understand and reproduce the experimental protocol.

Specifically, the repository provides:

* Documentation of the experimental protocol.
* Demographic information and questionnaire data for the 15 participants (anonymized).
* A complete example recording from one participant.
* Code to synchronize recordings from the different wearable devices.
* References to the associated publication and the Zenodo dataset.

# Repository Structure

```text
.
├── README.md
├── protocol/
│   └── protocol.pdf
├── demographics/
│   └── demographics.xlsx
├── example_data/
│   └── S2/
│       ├── S2_polar.csv
│       ├── S2_shimmer.csv
│       ├── S2_empatica.json
│       └── S2_psychopy_ts.xlsx
├── synchronization/
│   ├── sync.py
└── LICENSE
```

# Experimental Protocol

The experiment consisted of alternating relaxation and cognitive workload periods while physiological signals were continuously recorded. Participants first completed a resting baseline, followed by a **Paced Visual Serial Addition Test (PVSAT)**, a second resting period, and finally an **Italian Grammar Task**. After each cognitive task, participants completed the NASA Task Load Index (NASA-TLX) questionnaire to assess perceived workload. The protocol was administered through a Psychopy custom framework, handling durations and timestamps.

<p align="center">
  <img src="protocol/ExpProtNew.pdf" alt="Experimental protocol" width="900"/>
</p>

# Cognitive Tasks

## Paced Visual Serial Addition Test (PVSAT)

Participants were presented with a sequence of single-digit numbers and continuously added each new number to the previous one, selecting the result from an on-screen list. The task lasted 3 minutes and was designed to induce sustained cognitive load involving attention and working memory.

## Italian Grammar Task

Participants corrected grammatically incorrect Italian sentences by typing the revised versions using a keyboard. The task lasted 3 minutes and introduced realistic motor activity representative of everyday computer work.

# Physiological Signals

| Device               | Signals                 | Sampling Rate   | Example File        | Timestamp Format |
|----------------------|-------------------------|-----------------|---------------------|------------------|
| Polar H10            | ECG                     | 130 Hz          | `S2_polar.csv`      | Phone local time (`YYYY-MM-DDTHH:MM:SS.sss`), Europe/Rome timezone |
| Shimmer3 GSR+        | EDA, PPG, Accelerometer | 128 Hz          | `S2_shimmer.csv`    | Unix timestamp in (ms) |
| Empatica EmbracePlus | EDA, BVP                | 4 Hz, 64 Hz     | `S2_empatica.json`  | Unix timestamp in (µs) |


# PsychoPy Timestamp File

The `S2_psychopy_ts.xlsx` file contains Unix timestamps (in microseconds) together with their corresponding human-readable datetimes for each relevant event in the protocol.

| Column                                      | Description                                                 |
| ------------------------------------------- | ----------------------------------------------------------- |
| `participant`                               | Participant identifier.                                     |
| `exp_name`                                  | Name of the PsychoPy experiment.                            |
| `timestamp_start_exp` / `start_exp`         | Start of the experimental session.                          |
| `timestamp_relax1_start` / `relax1_start`   | Beginning of the first resting period.                      |
| `timestamp_relax1_end` / `relax1_end`       | End of the first resting period.                            |
| `timestamp_start_pasat` / `start_pasat`     | Beginning of the PVSAT task.                                |
| `timestamp_end_pasat` / `end_pasat`         | End of the PVSAT task.                                      |
| `timestamp_relax2_start` / `relax2_start`   | Beginning of the second resting period.                     |
| `timestamp_relax2_end` / `relax2_end`       | End of the second resting period.                           |
| `timestamp_start_grammar` / `start_grammar` | Beginning of the grammar task.                              |
| `timestamp_start_beep` / `start_beep`       | Timestamp of the auditory cue used during the grammar task. |
| `timestamp_end_grammar` / `end_grammar`     | End of the grammar task.                                    |
| `timestamp_end_exp` / `end_exp`             | End of the experimental session.                            |

These timestamps serve as reference markers for synchronizing data streams acquired from the Polar, Shimmer, and Empatica devices.
