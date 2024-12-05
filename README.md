# Replication package for "PRemo: A Dataset of Emotions on Pull Request Discussions"

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

## Project List Table

|  Main Programming  Language |             Project             |             Domain             | Created In |    Age   | LOC (Approx.) | \# Pull Requests | \# Contributors |
|:---------------------------:|:-------------------------------:|:------------------------------:|:----------:|:--------:|:-------------:|:----------------:|:---------------:|
| Java                        | spring-projects/spring-boot     | Development Framework          | 2012       | 12 years | 420k          | 6169             | 1074            |
|                             | spring-projects/spring-security | Security Framework             | 2012       | 12 years | 445k          | 2846             | 694             |
|                             | google/guice                    | Dependency Injection Framework | 2014       | 10 years | 106k          | 625              | 74              |
|                             | google/ExoPlayer                | Library                        | 2014       | 10 years | 479k          | 1191             | 239             |
|                             | google/guava                    | Library                        | 2014       | 10 years | 778k          | 2185             | 302             |
|                             | google/gson                     | Library                        | 2015       | 9 years  | 53k           | 996              | 147             |
|                             | google/dagger                   | Dependency Injection Framework | 2013       | 11 years | 167k          | 2287             | -               |
|                             | netflix/eureka                  | Service Registry               | 2012       | 12 years | 84k           | 864              | 108             |
|                             | netflix/hystrix                 | Fault Tolerance Library        | 2012       | 12 years | 78k           | 812              | 113             |
|                             | netflix/conductor               | Microservice                   | 2016       | 8 years  | 90k           | 1702             | 248             |
|                             | netflix/zuul                    | API Gateway                    | 2013       | 11 years | 73k           | 1195             | 57              |
|                             | JabRef/jabref                   | Graphical Library              | 2014       | 10 years | 235k          | 6901             | 630             |
|                             | mockito/mockito                 | Test Framework                 | 2012       | 12 years | 97k           | 1669             | 288             |
| JavaScript  (or Typescript) | vuejs/core                      | JS Framework                   | 2018       | 6 years  | 125k          | 4271             | 455             |
|                             | twbs/bootstrap                  | Web Framework                  | 2011       | 13 years | 44k           | 15110            | 1390            |
|                             | expressjs/express               | Node Framework                 | 2009       | 15 years | 23k           | 1273             | 307             |
|                             | facebook/react                  | Web Framework                  | 2013       | 11 years | 494k          | 14735            | 1656            |
|                             | sveltejs/svelte                 | Web Application                | 2016       | 8 years  | 84k           | 4594             | 670             |
|                             | ant-design/ant-design           | React Library                  | 2015       | 9 years  | 193k          | 16764            | 2091            |
|                             | angular/angular                 | Web Framework                  | 2014       | 10 years | 790k          | 26712            | 1882            |
|                             | d3/d3                           | Web Library                    | 2010       | 14 years | 20k           | 1170             | 132             |
|                             | microsoft/TypeScript            | Programming Language           | 2014       | 10 years | 3.4M          | 17314            | 771             |
|                             | mrdoob/three.js                 | JS Library                     | 2010       | 14 years | 426k          | 15603            | 1866            |
|                             | jestjs/jest                     | Test Framework                 | 2013       | 11 years | 120k          | 7165             | 1532            |
|                             | puppeteer/puppeteer             | Node API                       | 2017       | 7 years  | 76k           | 5428             | 485             |
| Python                      | tiangolo/fastapi                | Python Framework               | 2018       | 6 years  | 109k          | 3161             | 633             |
|                             | matplotlib/matplotlib           | Python Library                 | 2011       | 13 years | 249k          | 17823            | 1415            |
|                             | tinygrad/tinygrad               | Python Framework               | 2020       | 4 years  | 93k           | 3354             | 296             |
|                             | plotly/plotly.py                | Python Library                 | 2013       | 11 years | 902k          | 1617             | 238             |
|                             | pandas-dev/pandas               | Python Library                 | 2010       | 14 years | 612k          | 31839            | 3168            |
|                             | pydantic/pydantic               | Python Library                 | 2017       | 7 years  | 109k          | 3467             | 507             |
|                             | psf/requests                    | HTTP Library                   | 2011       | 13 years | 11k           | 2490             | 642             |
|                             | tensorflow/tensorflow           | ML Framework                   | 2015       | 9 years  | 1.2M          | 25164            | 3530            |
|                             | astropy/astropy                 | Library                        | 2011       | 13 years | 382k          | 10300            | 485             |
|                             | pallets/flask                   | Python Framework               | 2010       | 14 years | 17k           | 2524             | 715             |
|                             | ansible/ansible                 | Framework                      | 2012       | 12 years | 245k          | 50519            | 5000+           |

# Tool developed for the labeling 

The tool that was utilized to perform the labeling process is available as part of the replication package of the first study that was executed using the dataset, which is available at [https://github.com/opus-research/sentiment-replication](https://github.com/opus-research/sentiment-replication).
