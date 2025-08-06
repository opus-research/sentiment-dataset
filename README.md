# PRemo: A Dataset of Emotions Found on Pull Request Discussions

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.15810811.svg)](https://doi.org/10.5281/zenodo.15810811)

This repository contains the complete PRemo dataset, analysis tools, validation web application, and research findings.

Access the full paper [here](results/PRemo.pdf)

## Abstract

We introduce PRemo, a dataset of approximately 1,8k pull‑request messages from 36 open‑source projects, each annotated for discrete emotions, intensity levels and evaluator confidence via a two‑pass labelling process with and without context. Software engineers and neuroscientists conducted triple validation to ensure annotation reliability, and we report inter‑rater agreement metrics to demonstrate consistency. PRemo is publicly released to support fine‑grained emotion analysis in software engineering.

## Repository Structure

- [scripts](scripts): A Jupyter notebook, containing example code that can be used to analyze the dataset (including the data used in the paper) and a `requirements.txt` file that lists what is required to reproduce the project environment.
- [results](results): Analysis outputs including emotion frequency counts, sentiment polarity distributions, inter-rater agreement statistics, and comprehensive summary reports. Also includes the full paper in pdf version.
- [data](data): [dataset.json](data/dataset.json) with the complete dataset collected by the tool and detailed below.
    - The [data/labeling/](data/labeling/) subfolder contains the data that was used for the labeling process. Files are compressed (using 7-zip) due to file size constraints. It contains 4 files:
        - [data/labeling/all_comments.7z](data/labeling/all_comments.7z): json file with all of the comments that were mined before the sampling process.
        - [data/labeling/all_comments_with_sentiment.7z](data/labeling/all_comments_with_sentiment.7z): same file as above, but contains sentiment labels generated using SentiStrengthSE
        - [data/labeling/all_messages_ssse.7z](data/labeling/all_messages_ssse.7z): txt file containing all messages formatted in the way that SentiStrengthSE expects
        - [data/labeling/ssse_output.7z](data/labeling/ssse_output.7z): raw output of SentiStrengthSE containing the sentiment labels.
- [tool](tool): All scripts and requirements to replicate the web-based tool utilized to perform and collect the human labelling process.
- [screenshots](screenshots): Contain two screenshots that show how the pages in the labeling tool are structured.

## Dataset Schema for [dataset.json](data/dataset.json):

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

## Requirements

- Python 3 (tested using version 3.11)

## Reproducing the Analyses from the paper

1. Install dependencies using `pip install -r scripts/requirements.txt`

2. Run the analysis script on your terminal: `jupyter scripts/analysis.ipynb`
    -  You will also be able to execute it using any IDE capable of reading jupyter notebooks, such as VSCode, PyCharm, etc.
    -  If you want to avoid having to setup a local environment, we recommend running the notebook using Google Colab.

## Reproducing the Labeling Process

> [!CAUTION]
> To execute the labeling process, we created a tool called validatool. Since it was purpose built for this study, it was not build with extensibility in mind.
> You may also encounter bugs when trying to reproduce the study in different conditions (e.g., different number of participants) than that of our original study.
> The study was also manually monitored to make sure that the algorithm was allocating evaluators correctly for each message, and some manual changes had to be made to make sure the study protocol was being correctly followed, so your mileage may vary.

1. Navigate to the tool root folder: `cd ./tool/validatool`

2. Optional: We recommend that you create a virtual environment before proceeding: `python -m venv ./.venv/`. 
    - Activate by running the activate script created at `./.venv/Scripts`
    - The command to run the script may vary depending on your operating system and terminal:
        - Windows (cmd): `.venv\Scripts\activate.bat`
        - Linux/MacOs: `source ./venv/Scripts/activate`

3. Install dependencies: `pip install -r requirements.txt`

4. Create the database: `python manage.py migrate`

5. Create an admin user: `python manage.py createsuperuser`

6. Run the development server: `python manage.py runserver`
    - The tool will now be accessible to use via `http://localhost:8000`
    - However, we still need to setup the experiment data.

7.  Access the admin panel via `http://localhost:8000/admin/`
    - Login with the user created on step 5.
    - Create two groups with the default permissions: Neuro and Comp
    - Create the users that will participate in the validation. Set them in their correct groups after creation `Neuro` for neuroscientists and `Comp` for Software Engineers. The validation algorithm will not work without both types of users being present.
    - Go to the validation panel and create a new one. Use any title you want, add a guiding text (a text for training evaluators.)
        - The guiding text we utilized is located at [tool\validatool\guiding_text.md](tool\validatool\guiding_text.md).
    - For all evaluators create participation items in the database. Set the user and the validation and keep the item blank (there should be no items in the database for now).

8. Generate a random sample of messages to be added to the database.
    - First, unzip (using 7-zip) the [tool\validatool\scripts\data\all_comments_with_sentiment.7z](tool\validatool\scripts\data\all_comments_with_sentiment.7z) file. Do not create a subfolder when extracting the file.
    - After that, use the command `python manage.py runscript include_items_in_sentiment_validation` to create a random sample and include it in the database.
        - To tweak the ratio of messages (in terms of sentiment polarity assigned by SentiStrengthSE), manually change the values in the script.

9. Now, the users can just login in `http://localhost:8000` and participate in the validation. 
    - To login, you can either use the admin user created on step 5 or any of the users you have created for the participants in step 7.

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).  
Feel free to use, modify, and distribute it as permitted under the terms of this license.

## Papers that have utilized PRemo

- Coutinho, D., Cito, L., Lima, M.V., Arantes, B., Alves Pereira, J., Arriel, J., Godinho, J., Martins, V., Libório, P.V.C., Leite, L. and Garcia, A., 2024, June. " Looks Good To Me;-)": Assessing Sentiment Analysis Tools for Pull Request Discussions. In Proceedings of the 28th International Conference on Evaluation and Assessment in Software Engineering (pp. 211-221).
