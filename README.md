# PRemo: A Dataset of Emotions Found on Pull Request Discussions

This repository contains the complete PRemo dataset, analysis tools, validation web application, and research findings.

{ADD DOI}

Access the full paper [here](results/PRemo.pdf)

## Abstract

We introduce PRemo, a dataset of approximately 1,8k pull‑request messages from 36 open‑source projects, each annotated for discrete emotions, intensity levels and evaluator confidence via a two‑pass labelling process with and without context. Software engineers and neuroscientists conducted triple validation to ensure annotation reliability, and we report inter‑rater agreement metrics to demonstrate consistency. PRemo is publicly released to support fine‑grained emotion analysis in software engineering.

## Repository Structure

- [scripts](scripts): A Jupyter notebook, containing example code that can be used to analyze the dataset (including the data used in the paper) and a `requirements.txt` file that lists what is required to reproduce the project environment.
- [results](results): Analysis outputs including emotion frequency counts, sentiment polarity distributions, inter-rater agreement statistics, and comprehensive summary reports. Also includes the full paper in pdf version.
- [tool](tool): All scripts and requirements to replicate the web-based tool utilized to perform and collect the human labelling process.
- [data](data): [dataset.json](data/dataset.json) with the complete dataset collected by the tool and detailed below.

- #### Dataset Schema for [dataset.json](data/dataset.json):

```json
[
    {
        "project": "spring-boot",
        "message_url": "https://github.com/spring-projects/spring-boot/pull/21658#issuecomment-660726475",
        "raw_message": "did you get a chance to follow up on the issue? If not, I can take a look in the next 24hrs.",
        "part1_aggregate": { // Data for the first pass of our manual labelling, where the evaluators only had the text of the message.
            "polarity": "undefined",
            "avg_confidence": 3.3333333333333335,
            "agreement_type": "undefined"
        },
        "part2_aggregate": {  // Data for the second pass of our manual labelling, where the evaluators has access to the github link for the message, that includes more contextual information.
            "polarity": "neutral",
            "avg_confidence": 4.333333333333333,
            "agreement_type": "neuro_and_comp"
        },
        "discussion_polarity": "neutral", // OPTIONAL FIELD: Only exists if this was a case of total disagreement between evaluators. This field contains the polarity decided after they discussed the message.
        "individual_answers": [ // An array containing the individual response from each evaluator.
            {
                "part1": {
                    "polarity": "negative",
                    "emotions": [
                        "anger"
                    ],
                    "positive_intensity": 0, // Positive and negative intensities are separate, and the aggregate sentiment polarity is calculated based on this value.
                    "negative_itensity": 1,
                    "confidence": 2
                },
                "part2": {
                    "polarity": "neutral",
                    "emotions": [
                        "joy",
                        "anger"
                    ],
                    "positive_intensity": 1,
                    "negative_itensity": 1,
                    "confidence": 3
                },
                "user_type": "neuro" // May be "comp" or "neuro", representing a software engineer or a neuroscience student.
            },
    ...]
...]
```

## Reproducing the Study

- Tool

{ADD - tool part}

- Analysis of the data gathered by the tool.

    - 1. Install dependencies

    ```bash
   pip install -r scripts/requirements.txt
   ```

    - 2. Run the analysis script on your terminal - :

        - `python scripts/analysis.ipynb`

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).  
Feel free to use, modify, and distribute it as permitted under the terms of this license.

## Citation

If you use this repository or its data:

``` bibtex

```
