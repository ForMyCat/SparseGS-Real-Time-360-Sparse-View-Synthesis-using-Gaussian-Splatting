---
layout: project_page
permalink: /
title: "SparseGS: Real-Time 360° Sparse View Synthesis using Gaussian Splatting"
authors:
  - name: Haolin Xiong*
    url: https://www.linkedin.com/in/haolin-xiong-927221176
  - name: Sairisheek Muttukuru*
    url: https://www.linkedin.com/in/sairisheek/
  - name: Rishi Upadhyay
    url: https://web.cs.ucla.edu/~rishiu
  - name: Pradyumna Chari
    url: https://pradyumnachari.github.io
  - name: Achuta Kadambi
    url: https://www.ee.ucla.edu/achuta-kadambi
affiliations: University of California, Los Angeles
paper: https://arxiv.org/abs/2312.00206
code: https://github.com/ForMyCat/SparseGS

---
<div class="columns is-centered has-text-centered">
    <video width="700" height="300" playsinline controls loop autoplay muted>
      <source src=".\static\image\360_with_caption.mp4" type="video/mp4">
    </video>
</div>


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
        <figcaption>From left to right: GT, SparseNeRF, MipNeRF360, 3DGS, <b>SparseGS</b></figcaption>
    </figure>
</div>



## Background
Novel view synthesis has grown significantly in popularity recently thanks to the introduction of implicit 3D scene represenations such as NeRF. These techniques enable many downstream applications in fields ranging from robotics to entertainment. However, most of these techniques are limited by the number of training views required: many need up to 200 views which can be prohibitively high for real-world usage. Prior work has tackled this problem with sparse view techniques, but these almost entirely focus on forward-facing scenes and suffer from long training and inference times of NeRFs.

## Objective
We introduce a technique for real-time 360 sparse view synthesis by leveraging 3D Gaussian Splatting. The explicit nature of our scene representations allows to reduce sparse view artifacts with techniques that directly operate on the scene representation in an adaptive manner. Combined with depth based constraints, we are able to render high-quality novel views and depth maps for unbounded scenes.

<div style="text-align: left;">
    <figure>
        <img src=".\static\image\model_fig.png" alt="Pipeline" width="800" />
        <figcaption>Our proposed pipeline integrates depth and diffusion constraints, along with a floater pruning technique, to enhance the performance of few-shot novel view synthesis. During training, we render the alpha-blended depth, denoted as d<sup>alpha</sup> , and employ <b>Pearson correlation</b> to ensure its alignment with the monocularly estimated depth d<sup>pt</sup>. Furthermore, we impose a <b>score distillation sampling loss</b> on novel viewpoints to guarantee the generation of naturally-appearing images. At predetermined intervals, we execute <b>floater pruning</b> as described in Section 3 of our paper. In this illustration, new components that we introduce are highlighted in color, while the foundational 3D Gaussian Splatting pipeline is depicted in grey.</figcaption>
    </figure>
</div>


## Key Ideas
1. Leverage the explicit gaussian representation to directly remove unwanted sparse view artifacts such as “floaters” and “background collapse”
2. Use off-the-shelf depth estimation models to regularize novel view outputs
3. Apply softmax function to gaussian depth values for better depth rendering
4. Reconstruct regions with low coverage in training views with diffusion-model guidance
5. Use Depth Warping to create more training views

## Floater Removal Example
<div class="columns is-centered has-text-centered">
    <video width="700" height="300" playsinline controls loop autoplay muted>
      <source src=".\static\image\floater.mp4" type="video/mp4">
    </video>
</div>


## More Pictures
<div style="text-align: center;">
    <figure>
        <img src=".\static\image\base3dgs_1.png" alt="Ground Truth" width="250" />
        <img src=".\static\image\mipnerf_1.png" alt="mipnerf" width="250" />
        <img src=".\static\image\ours_1.png" alt="ours" width="250" />
        <img src=".\static\image\base3dgs_2.png" alt="Ground Truth" width="250" />
        <img src=".\static\image\mipnerf_2.png" alt="mipnerf" width="250" />
        <img src=".\static\image\ours_2.png" alt="ours" width="250" />
        <img src=".\static\image\base3dgs_3.png" alt="Ground Truth" width="250" />
        <img src=".\static\image\mipnerf_3.png" alt="mipnerf" width="250" />
        <img src=".\static\image\ours_3.png" alt="ours" width="250" />
        <img src=".\static\image\base3dgs_4.png" alt="Ground Truth" width="250" />
        <img src=".\static\image\mipnerf_4.png" alt="mipnerf" width="250" />
        <img src=".\static\image\ours_4.png" alt="ours" width="250" />
        <figcaption>From left to right: Base 3DGS, MipNeRF360, <b>SparseGS (Ours)</b></figcaption>
    </figure>
</div>

## More Videos (Updating)
<div class="columns is-centered has-text-centered">
    <video width="700" height="300" playsinline controls loop autoplay muted>
      <source src=".\static\image\vid_bonsai.mp4" type="video/mp4">
    </video>
</div>
<div class="columns is-centered has-text-centered">
    <video width="700" height="300" playsinline controls loop autoplay muted>
      <source src=".\static\image\vid_garden.mp4" type="video/mp4">
    </video>
</div>
<div class="columns is-centered has-text-centered">
    <video width="700" height="300" playsinline controls loop autoplay muted>
      <source src=".\static\image\vid_kitchen.mp4" type="video/mp4">
    </video>
</div>

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


## Citation
```
@article{xiong2023sparsegs,
  author    = {Xiong, Haolin and Muttukuru, Sairisheek and Upadhyay, Rishi and Chari, Pradyumna and Kadambi, Achuta},
  title     = {SparseGS: Real-Time 360° Sparse View Synthesis using Gaussian Splatting},
  journal   = {Arxiv},
  year      = {2023},
}
```
