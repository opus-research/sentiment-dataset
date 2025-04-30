# Replication package for "PRemo: A Dataset of Emotions Found on Pull Request Discussions"

The file [dataset.json](dataset.json) contains the dataset described in the paper.

## Dataset Schema:

```json
[
    {
        "project": "spring-boot",
        "message_url": "https://github.com/spring-projects/spring-boot/pull/21658#issuecomment-660726475",
        "raw_message": "did you get a chance to follow up on the issue? If not, I can take a look in the next 24hrs.",
        "part1_aggregate": { // Data for the first pass of our manual labeling, where the evaluators only had the text of the message.
            "polarity": "undefined",
            "avg_confidence": 3.3333333333333335,
            "agreement_type": "undefined"
        },
        "part2_aggregate": {  // Data for the second pass of our manual labeling, where the evaluators has access to the github link for the message, that includes more contextual information.
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

# Scripts

A Jupyter notebook, containing example code that can be used to analyze the dataset (including the data used in the paper), is available at [analysis.ipynb](analysis.ipynb).

# Tool developed for the labeling 

The web-based tool that was utilized to perform the labeling process is available as part of the replication package of the first study that was executed using the dataset, which is ommitted for blind review. The link will be provided after the paper is accepted.
