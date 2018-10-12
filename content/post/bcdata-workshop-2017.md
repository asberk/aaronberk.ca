+++
title = "Reflection: 2017 BC Data Science Workshop"
summary = """
A brief summary and some incomplete reflections from my time as the workshop TA for the 2017 BC Data Science workshop. 
"""
date = 2017-09-12T19:47:28-07:00
draft = false

# Tags and categories
# For example, use `tags = []` for no tags, or the form `tags = ["A Tag", "Another Tag"]` for one or more tags.
tags = ["data-science", "machine-learning"]
categories = []

# Featured image
# Place your image in the `static/img/` folder and reference its filename below, e.g. `image = "example.jpg"`.
[header]
image = "bcdata_banner.jpg"
image_preview = "bcdata_banner_small.jpg"
caption = "The 2017 BC Data Science Workshop"

+++

# Summary

This is a brief summary and some incomplete reflections from my time as the workshop TA for the 2017 BC Data Science Workshop. 

## About

The [BC Data Workshop](http://workshop.bcdata.ca/2017) was hosted August 9 &ndash; 25 in downtown Vancouver at UBC Robson Square, co-organized by myself, Brian Wetton and Lee Rippon from the IAM, with support from PIMS and SFU Mathematics.

The workshop featured a wide array of material from experts across the west coast, structured into three sections: a 3-day pre-workshop intensive; a week of introductory material; and a week-long data science project led by industry mentors.

## Pre-workshop

The pre-workshop was hosted by [Patrick Walls](http://www.math.ubc.ca/~pwalls/) and [Brian Wetton](https://www.math.ubc.ca/~wetton/). It covered software carpentry material like GitHub, introductory Python and bash, and Jupyter notebooks. It also covered elements of scientific computing and machine learning like gradient descent, principal component analysis, fast Fourier transforms, convex optimization and linear regression.

## First week

The mornings of the first week were comprised of introductory lectures by Isabell Konrad (UC Berkeley), Yinshan Zhao (BC Health) and Michael Reid (Amazon). Topics covered elements of machine learning and data science; hypothesis testing and experimental design; and modern software tools (SQL, Hadoop, Fink, Kafka, ElasticSearch, *etc.*). In the afternoons, participants completed mini-projects whose focus was related either to the morning material, or to tools that would be integral to a project in the second week. The mini-projects covered regression, neural networks, matrix completion, data wrangling and exploration, and distributed and parallel computing with Apache Spark and tensorflow on GPU.

## Second week

The mornings of the second week were comprised of "advanced topics" &mdash; featuring professors from UBC or SFU, speaking on elements of their research which rely on or develop tools from data science. The rest of the time was devoted to group projects. Teams of 5 &ndash; 7 worked on projects brought by industry mentors whose solutions would feature elements of data science. This included two kinds of image processing; nonlinear function approximation for video compression bitrate analysis; deep neural networks for genetics research; and analytics from vehicle time series messages.



# Opportunities and challenges

## My role as TA

It was most rewarding to learn how to think in different modes with
teams of diverse individuals working on very diverse projects. One
evening, I got to help create an interpretable way to balance highly
imbalanced data; the next morning I had to help design a way to train
a deep model using images on a [remote
server](https://github.com/bcdataca/bcsa-bcdata). After that, I
contributed to a brainstorming session on how to [best cluster
data](https://gist.github.com/asberk/1340166f2aa1b93607dae8645f4f9fb7)
that was too big for memory. In general, I got to contribute ideas for
project strategies, available software tools, and design/algorithm
troubleshooting.

## Designing mini-projects

An unintended consequence of the workshop saw me designing three of the five
mini-projects in the first week.

1. [Matrix completion](https://github.com/bcdataca/workshop-content17/tree/master/1-first-week/mini-projects/2-matrix-completion)
2. [Neural networks in keras](https://github.com/bcdataca/workshop-content17/tree/master/1-first-week/mini-projects/3-neural-networks)
3. [Parallel and distributed computing with `pyspark` and `tensorflow-gpu`](https://github.com/bcdataca/workshop-content17/tree/master/1-first-week/mini-projects/5-spark-aws)

Designing these consumed a lot of effort and time - too much given the other
organizational duties. Consequently, there are places where the work remains
unpolished. Nevertheless, designing these was a great opportunity to explore how
to communicate new concepts in an immersive, interactive way.

## Project duration

We may have imposed too great a constraint on the duration for which the teams
were able to work on their [industry
projects](http://workshop.bcdata.ca/2017/#projects). Effectively, they received
their projects Monday afternoon; had advanced lectures through the week; and had
to present on Friday afternoon. It's clear that longer duration would have
indeed allowed significantly greater progress on the teams' projects. That being
said, each of the teams made an impressive amount of progress that will be
discussed below.


# About the projects

## Data-driven modelling of video compression

This project had aggregate camera data and sought to use this data to determine
a function that could accurately predict the bitrate for given camera
settings. The group tried several convex optimization approaches, and settled on
a particular flavour of random forest, boasting accuracy well above what is
considered "industry standard".

## Risk-based platform for accdient prevention

I helped to design a skeleton for this project, wherein the team would take raw
photo data from BC Safety Authority inspections and use it to predict compliant
and non-compliant objects using a combination approach of active learning and
transfer learning. The training would have be performed by downloading batches
of images from an AWS S3 bucket, since there were too many images to fit on the
VM disk we were using. It is likely that such a model will require more complex
structure than a standard image recognition ConvNet, such as topic modelling or
LDA.

The team reduced the complexity of this task by classifying images of flowers
using a transfer learning approach. In this approach, these used bottlenecking
to generate feature vectors by running the images through the bottom several
layers of a VGG16 network. Then, they trained a binary classifier on this
markedly smaller feature space to discriminate between species of flowers. This
particular approach has immediate generalization potential to the more complex
problem of discerning compliant and non-compliant objects from inspection
photos.

## Elucidating enhancer-promoter gene expression using ConvNets

This group developed a convolutional neural network whose first layer filters,
after [agnostic] training, were composed of significant and known gene promoter
regions. This convolutional neural network was designed to predict the efficacy
of gene expression for particular enhancer-promoter pairs. This team made
significant progress in the time they had, and made steps toward a
reverse-complement invariant machine learning model.

## Data insights from vehicle time series messages

The goal of this project was to learn novel insights from vehicle time series
messages, logged by in-car devices that record the car's state, position,
etc. This team made significant progress toward the problem of discriminating
multiple drivers of the same vehicle. For this task, the team used Bayesian
methods and k-means.

## High-resolution shoreline data for flood protection and environmental conservation

This project sought to classify land type from photogrammetric drone image
data. The data was in the format of an unstructured sparse point cloud, listing
colour as well as latitude, longitude and elevation. The team took the approach
of looking at local variation in elevation, as well as point colour. The team
used an out-of-memory mini-batch k-means algorithm which clustered features
generated from a nearest neighbours tree. My own approach to this problem can be
[seen here](https://gist.github.com/asberk/1340166f2aa1b93607dae8645f4f9fb7).
