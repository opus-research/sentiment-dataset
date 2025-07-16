# Guide for manual label classification using sentiment analysis tools

## *Emotion model*

According to empirical research conducted by the authors and in similarity to previous researches, 6 emotions are established, broadly describing a total of 134 emotion names: love, anger, joy, sadness, fear and surprise (although the validity of this concept is questioned by Shaver and the other authors), which can also be seen as a two level distinction between positive (love, joy and sometimes surprise) and negative emotions (anger, sadness, fear and sometimes surprise). Each of these basic emotion categories contains a number of sub-clusters, classified as second level emotions by Calefato et al. (2017), representing generic core, context-specific representations of the basic emotions. Each of those secondary emotions also contains a number of third-level emotions, also as named by Calefato et al. (2017). Figure 1, adapted from Calefato, represents this hierarchical approach. It depicts an adaptation of Shaver et al. (1987) model of emotions and establishes the possible polarities of each emotion.

### Table 1 - Relationship between sentiment polarity and Shaver et al.’s emotion framework

|Emotion Polarity|Basic Emotions|Second Level Emotions|
|---|---|---|
|Positive|Love|Affection
|||Lust
|||Longing
||Joy|Cheerfulness
|||Zest
|||Contentment
|||Optimism
|||Pride
|||Enthrallment
|Negative|Anger|Irritation
|||Exasperation
|||Rage
|||Disgust
|||Envy
|||Torment
||Sadness|Suffering
|||Sadness
|||Disappointment
|||Shame
|||Neglect
|||Sympathy
||Fear|Horror
|||Nervousness
|Conxtext Dependant|Surprise|Surprise

Each emotion can be paired with a polarity: positive or negative. The concept of neutrality is not defined by this theoretical approach. However, neutral labels have been utilized in previous research (Calefato et al., 2017; Ortu et al., 2014). These studies established that neutral denotes the absence of emotion. Since this guide takes a dimensional approach to sentiment analysis, our neutral label will encompass both the absence of emotion and the cases in which the difference between the negative and positive scale equals zero. 

## Specific Guidelines

### Step 1 - Introduction

You are invited to participate in our sentiment classification study of texts taken from selected open-source Github repositories. The objective of this study is to categorize and analyze emotions and their polarity in technical documents authored by developers during their online interactions. **We recommend that for each day you classify up to 14 messages, with a total time limit of two consecutive hours.**

### Step 2 - Classification

You will receive a random message selected by random sampling. Your unit of work for now is the entire message available, limited to the content exposed in it. Your unit of work for now is the commenter’s message available, limited to the content expressed by them, excluding the interactions made by other users. For each post, you must indicate three aspects: (1) whether the message has any emotions, (2) which it conveys among the basic ones and (3) the intensity of the polarity present. Classify according to Table 1.

If you can’t identify any emotion, indicate so and that will be accounted as a neutral classification. The polarity of each emotion is predefined as shown in Table 1. Indicate its polarity in both the negative and positive spectrum, using a 4-point scale of intensity for each (Table 2). If there are equivalent but opposing emotions (i.e. negative 3 and a positive 3 at the same time), this will be considered a case of neutrality. It is important to note that “surprise” can manifest itself with a positive or negative polarity, at the discretion of the evaluator.

After this step, a similar analysis must be performed. This time, consider the entire context of the message. Context qualifies as any message in interactions that occurred in the same conversation contemplating dates prior and subsequent to the analyzed message.

### Table 2 - Polarity and confidence classification dictionary

|Construct|Classification|Meaning
|---|---|---|
|(Positive or Negative)|1|Slightly Present
||2|Moderately Present
||3|Very Present
||	4|Extremely Present

|Construct|Classification|Meaning
|---|---|---|
|Confidence|1|Very Little
||2|Little
||3|Moderate
||4|Strong
||5|Very Strong

Note that some phrases and expressions are common among the messages; two examples are the words "sorry" and "thanks." In order to maintain consistency, these expressions are often classified as conveying sadness and joy, respectively.

### Step 3 - Registration

Remember to enter in the annotation field which basic emotions you identified and how the current message presents itself in both the positive and negative scale, following the classification criteria expressed in Step 2. Please note in the respective field if you think it is a case of neutrality. Certify how confident you are in your answer, according to a 4 point scale (Table 2). To register your answer, just press the submit button in the form where you are performing the task. Below you can find some examples of possible registrations.

#### Example 1: positive polarity

> Thanks again @izeye!

|Are there emotions in this sentence?|What emotions can you identify in this sentence?|How would you evaluate the sentiment in the sentence?|How confident are you in the answers for this part?
|---|---|---|---|
|Yes|Joy|Positive - (4) Extremely present|(5) Very strong

#### Example 2: negative polarity

> Closing this PR. I can't run the integration tests on my computer. They always fail. Feel free to use the code if you wish. It takes too much time to try to submit PRs to this project and I can't justify spending any more time trying to make this work.

|Are there emotions in this sentence?|What emotions can you identify in this sentence?|How would you evaluate the sentiment in the sentence?|How confident are you in the answers for this part?
|---|---|---|---|
|Yes|Anger and Sadness|Negative - (4) Extremely present|(5) Very strong

#### Example 3: both polarities present

> Yea, that one was weird since @BindsInstance isn't actually "released" yet but I "did" it

|Are there emotions in this sentence?|What emotions can you identify in this sentence?|How would you evaluate the sentiment in the sentence?|How confident are you in the answers for this part?
|---|---|---|---|
|Yes|Positive surprise and Fear.|Positive - (3) Very present \| Negative - (2) Moderately present|(3) Neutral

#### Example 4: neutrality


> @tomjenkinson 1.4.x uses 5.3 and we won't upgrade to 5.5.1 in a maintenance release. You can however override the version as described in the doc.


|Are there emotions in this sentence?|What emotions can you identify in this sentence?|How would you evaluate the sentiment in the sentence?|How confident are you in the answers for this part?
|---|---|---|---|
|No|-|-|(4) Moderately

#### Example 5: neutrality

> @igor-suhorukov thanks, I've merged your contribution with a polish commit. If you run the maven build, those formatting failures will show up with an instruction on how to fix them.

|Are there emotions in this sentence?|What emotions can you identify in this sentence?|How would you evaluate the sentiment in the sentence?|How confident are you in the answers for this part?
|---|---|---|---|
|Yes|Joy and Anger|Positive - (2) Moderately present \| Negative - (2) Moderately present|(4) Moderately

#### Additional concerns

There are some situations where the message may have to be posteriorly excluded. This should be reported at the last box (“**Is there a reason for this message to be excluded? If there isn't, leave this field blank.**”). Sometimes, the criteria will be left entirely at the discretion of the evaluator. However, two frequent examples of these situations are if the commenter is a bot or either the message or the context is primarily in another language. 

## References

B. Lin, F. Zampetti, G. Bavota, M. Di Penta, M. Lanza and R. Oliveto, **"Sentiment Analysis for Software Engineering: How Far Can We Go?**," _2018 IEEE/ACM 40th International Conference on Software Engineering (ICSE)_, Gothenburg, Sweden, 2018, pp. 94-104, doi: 10.1145/3180155.3180195.

Calefato, F., Lanubile, F., Maiorano, F., & Novielli, N. (2017). Sentiment Polarity Detection for Software Development. In Empirical Software Engineering (Vol. 23, Issue 3, pp. 1352–1382). Springer Science and Business Media LLC. https://doi.org/10.1007/s10664-017-9546-9

Jin Ding, Hailong Sun, Xu Wang, and Xudong Liu. 2018. **Entity-level sentiment analysis of issue comments.** In Proceedings of the 3rd International Workshop on Emotion Awareness in Software Engineering (SEmotion '18). Association for Computing Machinery, New York, NY, USA, 7–13. [](https://doi.org/10.1145/3194932.3194935) [https://doi.org/10.1145/3194932.3194935](https://doi.org/10.1145/3194932.3194935).

K, K. P. (2020, August 09). **A Literature Review on Application of Sentiment Analysis Using Machine Learning Techniques**. International Journal of Applied Engineering and Management Letters (IJAEML), 4(2), 41-77. [https://doi.org/10.5281/zenodo.3985353](https://doi.org/10.5281/zenodo.3985353).

Kastrati, Z., Imran, A. S., & Kurti, A. (2020). **Weakly Supervised Framework for Aspect-Based Sentiment Analysis on Students’ Reviews of MOOCs**. Institute of Electrical and Electronics Engineers (IEEE). [https://doi.org/10.1109/access.2020.3000739](https://doi.org/10.1109/access.2020.3000739).

Mishev, K., Gjorgjevikj, A., Vodenska, I., Chitkushev, L. T., & Trajanov, D. (2020). **Evaluation of Sentiment Analysis in Finance: From Lexicons to Transformers**. In IEEE Access (Vol. 8, pp. 131662–131682). Institute of Electrical and Electronics Engineers (IEEE). [https://doi.org/10.1109/access.2020.3009626](https://doi.org/10.1109/access.2020.3009626).

Murgia, Alessandro & Tourani, Parastou & Adams, Bram & Ortu, Marco. (2014). **Do developers feel emotions? An exploratory analysis of emotions in software artifacts**. 11th Working Conference on Mining Software Repositories, MSR 2014 - Proceedings. 10.1145/2597073.2597086.

Nicole Novielli, Fabio Calefato, Davide Dongiovanni, Daniela Girardi, and Filippo Lanubile. 2020. **Can We Use SE-specific Sentiment Analysis Tools in a Cross-Platform Setting?** In Proceedings of the 17th International Conference on Mining Software Repositories (MSR '20). Association for Computing Machinery, New York, NY, USA, 158–168. [](https://doi.org/10.1145/3379597.3387446) [https://doi.org/10.1145/3379597.3387446](https://doi.org/10.1145/3379597.3387446).

Ortu, Marco & Murgia, Alessandro & Destefanis, Giuseppe & Tourani, Parastou & Tonelli, Roberto & Marchesi, Michele & Adams, Bram. (2016). **The Emotional Side of Software Developers in JIRA**. 10.1145/2901739.2903505.

Shaver P, Schwartz J, Kirson D, O’Connor C (1987) **Emotion knowledge: Further exploration of a prototype approach**. Journal of Personality and Social Psychology 52(6):1061–1086, DOI 10.1037//0022- 3514.52.6.1061, URL [http://dx.doi.org/10.1037//0022-3514.52.6.1061](http://dx.doi.org/10.1037/0022-3514.52.6.1061)

T. Ahmed, A. Bosu, A. Iqbal and S. Rahimi, "**SentiCR: A customized sentiment analysis tool for code review interactions**," _2017 32nd IEEE/ACM International Conference on Automated Software Engineering (ASE)_, Urbana, IL, USA, 2017, pp. 106-111, doi: 10.1109/ASE.2017.8115623.