---
layout: project_page
permalink: /
title: "SparseGS: Real-Time 360° Sparse View Synthesis using Gaussian Splatting"
authors:
  - name: Haolin Xiong
    url: https://www.linkedin.com/in/haolin-xiong-927221176
  - name: Sairisheek Muttukuru
    url: https://www.example.com/author2
  - name: Rishi Upadhyay
    url: https://web.cs.ucla.edu/~rishiu
  - name: Pradyumna Chari
    url: https://pradyumnachari.github.io
  - name: Achuta Kadambi
    url: https://www.ee.ucla.edu/achuta-kadambi
affiliations: University of California, Los Angeles
paper: 
video: 
code: 

---

<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
The problem of novel view synthesis has grown significantly in popularity recently with the introduction of Neural Radiance Fields (NeRFs) and other implicit scene representation methods. A recent advance, 3D Gaussian Splatting (3DGS), leverages an explicit representation to achieve real-time rendering with high-quality results. However, 3DGS still requires an abundance of training views to generate a coherent scene representation. In few shot settings, similar to NeRF, 3DGS tends to overfit to training views, causing background collapse and excessive floaters, especially as the number of training views are reduced. We propose a method to enable training coherent 3DGS-based radiance fields of 360 scenes from sparse training views. We find that <b>using naive depth priors is not sufficient</b> and integrate depth priors with generative and explicit constraints to reduce background collapse, remove floaters, and enhance consistency from unseen viewpoints. Experiments show that our method outperforms base 3DGS by up to <b>30.5%</b> and NeRF-based methods by up to <b>15.6%</b> in LPIPS on the MipNeRF-360 dataset with substantially less training and inference cost.
        </div>
    </div>
</div>

---

<div style="text-align: center;">
    <figure>
        <img src=".\static\image\teaser_gt.JPG" alt="Ground Truth" width="150" />
        <img src=".\static\image\teaser_sparsenerf.jpg" alt="SparseNeRF" width="150" />
        <img src=".\static\image\teaser_mipnerf360.png" alt="MipNeRF360" width="150" />
        <img src=".\static\image\teaser_base3DGS.png" alt="3DGS" width="150" />
        <img src=".\static\image\teaser_ours.png" alt="Ours" width="150" />
        <figcaption>From left to right: GT, SparseNeRF, MipNeRF360, 3DGS, Ours</figcaption>
    </figure>
</div>



## Background
The paper "On Computable Numbers, with an Application to the Entscheidungsproblem" was published by Alan Turing in 1936. In this groundbreaking paper, Turing introduced the concept of a universal computing machine, now known as the Turing machine.

## Objective
Turing's main objective in this paper was to investigate the notion of computability and its relation to the Entscheidungsproblem (the decision problem), which is concerned with determining whether a given mathematical statement is provable or not.

<div style="text-align: left;">
    <figure>
        <img src=".\static\image\model_flowchart.png" alt="Ground Truth" width="800" />
        <figcaption>Our proposed pipeline integrates depth and diffusion constraints, along with a floater pruning technique, to enhance the performance of few-shot novel view synthesis. During training, we render the alpha-blended depth, denoted as d<sup>alpha</sup> , and employ <b>Pearson correlation</b> to ensure its alignment with the monocularly estimated depth d<sup>pt</sup>. Furthermore, we impose a <b>score distillation sampling loss</b> on novel viewpoints to guarantee the generation of naturally-appearing images. At predetermined intervals, we execute <b>floater pruning</b> as described in Section 3 of our paper. In this illustration, new components that we introduce are highlighted in color, while the foundational 3D Gaussian Splatting pipeline is depicted in grey.</figcaption>
    </figure>
</div>


## Key Ideas
1. 
2. 
3. 


*Figure 1: A representation of a Turing Machine. Source: [Wiki](https://en.wikipedia.org/wiki/Turing_machine).*

## Table: Some sparse-view NeRF baseline comparisons on the MipNeRF360 dataset

| Model         | PSNR ↑   | SSIM ↑   | LPIPS ↓ | Runtime\* (h) | Render FPS |
|---------------|----------|----------|---------|-------------|------------|
| SparseNeRF    | 11.5638  | 0.3206   | 0.6984  | 4           | 1/120      |
| Base 3DGS     | 15.3840  | 0.4415   | <u>0.5061</u>  | 0.5         | 30         |
| Mip-NeRF 360  | **17.1044**  | <u>0.4660</u>   | 0.5750  | 3           | 1/120      |
| RegNeRF       | 11.7379  | 0.2266   | 0.6892  | 4           | 1/120      |
| ViP-NeRF      | 11.1622  | 0.2291   | 0.7132  | 4           | 1/120      |
| Ours          | <u>16.6898</u>  | **0.4899**   | **0.4849**  | 0.75        | 30         |

We use 12 images for each scene.
\* Runtimes are recorded on one RTX3090.


## Contribution
Turing's paper laid the foundation for the theory of computation and had a profound impact on the development of computer science. The Turing machine became a fundamental concept in theoretical computer science, serving as a theoretical model for studying the limits and capabilities of computation. Turing's work also influenced the development of programming languages, algorithms, and the design of modern computers.

## Citation
```
@article{xiong2023sparsegs,
  author    = {Xiong, Haolin and Muttukuru, Sairisheek and Upadhyay, Rishi and Chari, Pradyumna and Kadambi, Achuta},
  title     = {SparseGS: Real-Time 360° Sparse View Synthesis using Gaussian Splatting},
  journal   = {Arxiv},
  year      = {2023},
}
```
