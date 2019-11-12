---
layout: post
author:
- Huaming Chen
subtitle: Part I
title: Survey for Anomaly Detection
---

-- Huaming 2018.09.18

Background
==========

Definition
----------

Definition

-   Anomaly detection

    -   An important problem regarding finding patterns in data, which
        do not conform to expected behavior

    -   These patterns, or anomalies in data will translate to
        significant actionable information.

    -   **Anomalies**, **outliers**, discordant observations,
        exceptions, aberrations etc\...

-   Extensive use in a wide variety of applications

    -   Fraud detection for credit cards, insurance or health care

    -   intrusion detection for cyber-security

    -   fault detection in safety critical systems

-   Originally started from statistical community [^1]

Definition Anomalies are patterns in data that do not conform to a well
defined notion of normal behavior

![image]({{ site.baseurl }}/images/20180918_1.png)

Definition Figure 1 illustrates anomalies in a simple 2-dimensional data
set. **N_1** and **N_2** are normal regions, while **O_1** and **O_2** and
region **O_3** are anomalies.\
Observing or detecting an anomaly is mostly via interesting features:

-   Malicious activity in fraud detection, abnormal sequence patterns of
    real life relevance

-   All of the reasons have a common characteristic that they are
    interesting to the analyst

Definition Anomaly detection is related to but distinct from noise
removal and noise accommodation.

-   Noise is defined as a signal in data which is not of interest but
    acting as hindrance to data analyst.

-   Thus, noise removal is referred to removing unwanted signal in data
    before any data analysis.

-   Noise accommodation is to immunize a statistical model estimation
    against anomalous observations.

Definition Novelty detection is another topic which may be overlapped
with anomaly detection:

-   It is to detect previously unobserved patterns in the data, may be
    new topic or new group.

-   The novel patterns are added to the normal model once detected

-   Anomalies will be sometimes hard to be defined as one specific
    group, and are also undesired for the information translation.

Types and challenges
--------------------

Types of Anomalies Anomalies could be broadly categorized as:

-   Point anomalies

    -   an individual data instance. Taking credit card fraud detection
        as example, *amount spent* is used as the feature for
        simplicity.

-   Contextual anomalies

    -   also termed as conditional anomaly. Imaging temperature around
        $30^{\circ}$ may be considered as normal during summer, it is
        taken as anomaly during winter.

-   Collective anomalies

    -   A group of data instances collectively define the anomaly
        characteristics, which mostly involve temporal attribute.

Challenges Though anomalies detection has been extensively researched,
in most cases, this topic is answered dependently:

-   Difficult a general normal region which may encompasses every
    possible normal behavior

-   Both normal behavior and anomalies are evolving at all times, which
    means a current notion may not be sufficient

-   The availability of labeled data for training/validation of models

-   Noise from the data may impair the model and the performance

Solutions Most of the existing anomaly detection techniques solve a
specific formulation of the problem.

-   Nature of the data

-   Availability of labeled data

-   Type of anomalies

Approaches
==========

Data in and out from models
---------------------------

Data Labels It is often highly expensive to obtaining labeled data which
is accurate as well as representative of all types of patterns.

-   Mostly data of normal patterns are easy to obtain

-   New types of anomalies may arise

-   Anomalies are rare in specific areas, such as airline industry

Data Labels

-   Supervised anomaly detection:

    -   Imbalanced issue: anomalies are far fewer compared to normal
        instances -- down sampling normal instances or up sampling
        anomalies

    -   Labels obtaining -- injecting artificial anomalies in normal
        data sets

-   Semi-supervised anomaly detection: only normal data are available

-   Unsupervised anomaly detection: basic assumption is normal instances
    are far more than anomalies

Output for anomaly detection

-   **Scores:** The output is mostly a ranked list of anomalies

-   **Labels:** The output is mostly a binary label regarding normal or
    anomalous

Techniques
----------

Statistical Models **Normal data instances occur in high probability
regions of a stochastic model, while anomalies occur in the low
probability regions of the stochastic model.**\
Statistical techniques fit a statistical model (usually for normal
behavior) to the given data and then apply a statistical inference test
to determine if an unseen instance belongs to this model or not.
Instances that have a low probability to be generated from the learnt
model, based on the applied test statistic, are declared as anomalies.

Statistical Models

-   Gaussian Model

    -   box plot rule: univariate scalars

    -   Grubb's test: univariate scalars

    -   Extensions: Mahalanobis distance for test instance $X$ to reduce
        multivariate observations to univariate scalars

-   Regression Model

-   Mixture of Parametric Distributions based Model

Classification based techniques **Assumption: A classifier that can
distinguish between normal and anomalous classes can be learnt in the
given feature space.**\

-   Multi-class: Data contains labeled instances belonging to multiple
    normal classes.

    -   A instance is considered as anomalies once it is not classified
        as one of the normal classes

-   One-class: Data for training have only one class label.

    -   one-class SVMs, one-class Kernel Fisher Discriminants

Classification based techniques

-   Neural Network based solutions: MLP, Replicator Neural Networks

-   Bayesian Networks based solutions

-   SVM based solutions

-   Rule based solutions

Nearest Neighbor based techniques Computing distance or similarity
between two data instances with different ways. Mostly, it is
categorized by two directions: distance to $k_th$ nearest neighbor,
relative density.

-   Continuous attributes: euclidean distance is popular

-   Categorical attributes: simple matching coefficient is often used

-   Multivariate data instances: Combination of the distances for each
    attribute

Nearest Neighbor based techniques

-   Local outlier factor (LOF): an anomaly score to a given data
    instance

-   Connectivity-based outlier factor (COF): variation of the LOF

Summary
=======

Summary

-   Notion of Anomalies Detection

-   Classification of Anomalies Detection

-   Techniques for Anomalies Detection

Todo

-   Define the requirements for anomalies detection

-   Characteristics of the available data

-   Techniques evaluations: most of the techniques could be found from
    scikit-learn and open source code

[^1]: Edgeworth, F. Y. 1887. On discordant observations. Philosophical
    Magazine 23, 5, 364-375.

Reference 
1. Chandola, Varun, Arindam Banerjee, and Vipin Kumar.
\"Anomaly detection: A survey.\" ACM computing surveys (CSUR) 41.3
(2009): 15.
2. Sestito, Guilherme Serpa, et al. \"A Method for Anomalies Detection
in Real-Time Ethernet Data Traffic Applied to PROFINET.\" IEEE
Transactions on Industrial Informatics 14.5 (2018): 2171-2180.
3. Stojanovic, Ljiljana, et al. \"Big-data-driven anomaly detection in
industry (4.0): An approach and a case study.\" Big Data (Big Data),
2016 IEEE International Conference on. IEEE, 2016.
