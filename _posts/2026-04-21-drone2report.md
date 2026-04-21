---
layout: post
title: "Article published in the journal *Drones*"
author: "Filippo Biscarini"
date: "2026-04-21"
categories: ['PUBLICATIONS']
tags: ['drones','article','software', 'computer vision']
---

Our **Technical Note** "**drone2report: A Configuration-Driven Multi-Sensor Batch-Processing Engine for UAV-Based Plot Analysis in Precision Agriculture**"
has been published in the journal *Drones* (on-line version [here](https://www.mdpi.com/2504-446X/10/4/301)).

This article presents the functionalities of the software [drone2report](https://github.com/ne1s0n/drone2report), developed within the Polyploidbreeding 4.0 project.
Drone2report reads images from drone (UAV: unmanned aerial vehicle) phenotyping and does several things, e.g. calculating vegetation indices or implementing machine-learning classification or predictive models.

<a href="/assets/img/posts/workflow.png"><img src="/assets/img/posts/workflow.png" alt="Workflow"></a>
<div class="caption"><b>Figure</b>: General workflow. Panel (a): drones capture raw, partial images of the field (depending on the mounted sensors). All images from a single flight are collated in a unique orthomosaic. Panel (b): orthomosaics coming from one or more sensors, together with a shape file that specifies the ROIs, enter drone2report and are converted to an internal dataset object. Panel (c): all datasets are input, in turn, to all queued tasks, each task producing its specific output (e.g., tables, other images, etc.).</div>



