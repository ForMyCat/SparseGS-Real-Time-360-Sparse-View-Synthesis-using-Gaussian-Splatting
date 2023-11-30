---
layout: project_page
permalink: /

title: On Computable Numbers, with an Application to the Entscheidungsproblem
authors:
    A. M. Turing
affiliations:
    King's College, Cambridge
paper: https://www.cs.virginia.edu/~robins/Turing_Paper_1936.pdf
video: https://www.youtube.com/results?search_query=turing+machine
code: https://github.com/topics/turing-machines
data: https://huggingface.co/docs/datasets
---

<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
The problem of novel view synthesis has grown significantly in popularity recently with the introduction of Neural Radiance Fields (NeRFs) and other implicit scene representation methods. A recent advance, 3D Gaussian Splatting (3DGS), leverages an explicit representation to achieve real-time rendering with high-quality results. However, 3DGS still requires an abundance of training views to generate a coherent scene representation. In few shot settings, similar to NeRF, 3DGS tends to overfit to training views, causing background collapse and excessive floaters, especially as the number of training views are reduced. We propose a method to enable training coherent 3DGS-based radiance fields of 360 scenes from sparse training views. We find that using naive depth priors is not sufficient and integrate depth priors with generative and explicit constraints to reduce background collapse, remove floaters, and enhance consistency from unseen viewpoints. Experiments show that our method outperforms base 3DGS by up to 30.5% and NeRF-based methods by up to 15.6% in LPIPS on the MipNeRF-360 dataset with substantially less training and inference cost.
        </div>
    </div>
</div>

---


## Background
The paper "On Computable Numbers, with an Application to the Entscheidungsproblem" was published by Alan Turing in 1936. In this groundbreaking paper, Turing introduced the concept of a universal computing machine, now known as the Turing machine.

## Objective
Turing's main objective in this paper was to investigate the notion of computability and its relation to the Entscheidungsproblem (the decision problem), which is concerned with determining whether a given mathematical statement is provable or not.


## Key Ideas
1. 
2. 
3. 

![Turing Machine](/static/image/Turing_machine.png)

*Figure 1: A representation of a Turing Machine. Source: [Wiki](https://en.wikipedia.org/wiki/Turing_machine).*

## Table: Comparison of Computable and Non-Computable Numbers

| Model         | PSNR ↑   | SSIM ↑   | LPIPS ↓ | Runtime (h) | Render FPS |
|---------------|----------|----------|---------|-------------|------------|
| SparseNeRF    | 11.5638  | 0.3206   | 0.6984  | 4           | 1/120      |
| Base 3DGS     | 15.3840  | 0.4415   | <u>0.5061</u>  | 0.5         | 30         |
| Mip-NeRF 360  | **17.1044**  | <u>0.4660</u>   | 0.5750  | 3           | 1/120      |
| RegNeRF       | 11.7379  | 0.2266   | 0.6892  | 4           | 1/120      |
| ViP-NeRF      | 11.1622  | 0.2291   | 0.7132  | 4           | 1/120      |
| Ours          | <u>16.6898</u>  | **0.4899**   | **0.4849**  | 0.75        | 30         |

He used the concept of a universal Turing machine to prove that the set of computable functions is recursively enumerable, meaning it can be listed by an algorithm.

## Significance
Turing's paper laid the foundation for the theory of computation and had a profound impact on the development of computer science. The Turing machine became a fundamental concept in theoretical computer science, serving as a theoretical model for studying the limits and capabilities of computation. Turing's work also influenced the development of programming languages, algorithms, and the design of modern computers.

## Citation
```
@article{turing1936computable,
  title={On computable numbers, with an application to the Entscheidungsproblem},
  author={Turing, Alan Mathison},
  journal={Journal of Mathematics},
  volume={58},
  number={345-363},
  pages={5},
  year={1936}
}
```
