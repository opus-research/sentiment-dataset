# Replication package for "From Code to Emotion: A Dataset of Pull Request Discussions for Advancing Emotion Analysis in Software Engineering"

The file [dataset.json](dataset.json) contains an semi-anonymized version (no project names or links to the original messages, but messages may contain links or usernames) of the dataset described in the paper. In case it is needed, the full version can be requested for research via e-mail (after blind review). 

Dataset Schema:

```json
[
    {
        "raw_message": "did you get a chance to follow up on the issue? If not, I can take a look in the next 24hrs.",
        "part1_aggregate": {
            "polarity": "undefined",
            "avg_confidence": 3.3333333333333335,
            "agreement_type": "undefined"
        },
        "part2_aggregate": {
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
                    "positive_intensity": 0,
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
                "user_type": "neuro"
            },
    ...]
...]
```

Additional artifacts, such as the scripts utilized to build the dataset and documentation about the structure of the dataset, will also be available after blind review, when they will be disponibilized in a permanent (and DOI compatible) file sharing solution such as Zenodo. We will also provide python code that is able to easily parse the data in the dataset.
