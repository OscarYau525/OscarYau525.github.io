---
# Leave the homepage title empty to use the site title
title: 'Yau, Chung Yiu'
date: 2025-9-24
type: landing

sections:
  # About block
  - block: about.avatar
    id: about
    content:
      title: About Me
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
    design:
      biography:
        style: ''
  # Paper Highlight block (combined)
  - block: paper_highlight
    content:
      title: "Highlights"
      papers:
        - title: "RoSTE: An Efficient Quantization-Aware Supervised Fine-Tuning Approach for Large Language Models"
          link: "https://arxiv.org/pdf/2502.09003"
          year: "2025"
          authors: "Quan Wei, Chung-Yiu Yau, Hoi-To Wai, Yang (Katie) Zhao, Dongyeop Kang, Youngsuk Park, Mingyi Hong"
          code: "https://github.com/OptimAI-Lab/RoSTE"
          slides: "uploads/roste_slides.pdf"
          summary: |
            tldr: This paper re-emphasizes the role of incoherence processing in Quantization-Aware Training by identifying rotated quantization as a bias-reduction for straight-through estimated gradient training. Our algorithm achieves state-of-the-art 4-bits weight-activation quantized fine-tuned LLMs from full-precision pre-trained models such as Llama and Pythia.
          figures:
            - src: "uploads/roste_exp1.svg"
              alt: "RoSTE Exp1"
            - src: "uploads/roste_exp1_qwen.svg"
              alt: "RoSTE Exp1 Qwen"
            - src: "uploads/roste_exp2.svg"
              alt: "RoSTE Exp2"
          caption: "RoSTE surpasses the performance of SOTA quantization methods on fine-tuning benchmark. Horizontal axis represents the total amount of hours needed to fine-tune pre-trained LLMs on a server of 8 × A100 NVIDIA GPUs."
        - title: "A Stochastic Approximation Approach for Efficient Decentralized Optimization on Random Networks"
          class: "dist-opt"
          link: "https://arxiv.org/pdf/2410.18774v2"
          year: "2025"
          authors: "Chung-Yiu Yau, Haoming Liu, Hoi-To Wai"
          code: "https://github.com/OscarYau525/FSPDA"
          slides: "uploads/FSPDA_slides_asilomar.pdf"
          summary: |
            tldr: We propose the first asynchronous decentralized optimization algorithm that utilizes the primal-dual framework on random graph and randomly sparsified communications. Our algorithms operate in practical scenario such as decentralized systems with unstable pairwise communication and asynchronous gradient computation.
          figures:
            - src: "uploads/fspda_mnist_grad_norm.svg"
              alt: "FSPDA Grad Norm"
            - src: "uploads/fspda_mnist_consensus_error.svg"
              alt: "FSPDA Consensus Error"
          caption: "This figure demonstrates how FSPDA-SA tolerates different levels of sparse communication on sparse random graph while converging to the same magnitude of stationarity, due to the transient effect of sparsity error. Only consensus error is dominantly affected by the sparsity error."
  # Paper block
  - block: paper
    content:
      title: "Publications"
      papers:
      - title: "Decentralized Stochastic Optimization over Unreliable Networks via Two-timescales Updates"
        class: "dist-opt"
        link: "https://arxiv.org/pdf/2502.08964"
        year: "2025"
        authors: "Haoming Liu, Chung-Yiu Yau, Hoi-To Wai"
        summary: "tldr: This paper extends the random graph primal-dual decentralized optimization algorithm (FSPDA) with non-linear noisy communication compression such as quantization with noise. This algorithm is the first algorithm capable of non-linear communication and random graph gossip."
      - title: "EMC^2: Efficient MCMC Negative Sampling for Contrastive Learning with Global Convergence"
        link: "https://raw.githubusercontent.com/mlresearch/v235/main/assets/yau24a/yau24a.pdf"
        year: "2024"
        authors: "Chung-Yiu Yau, Hoi-To Wai, Parameswaran Raman, Soumajyoti Sarkar, Mingyi Hong"
        code: "https://github.com/amazon-science/contrastive_emc2"
        poster: "uploads/emc2_poster.pdf"
        video: "https://www.youtube.com/watch?v=kFIQwwkt4zw"
        slides: "uploads/emc2_slides.pdf"
        summary: "tldr: We apply MCMC sampling to draw negative samples for optimizing the global contrastive loss, an upper bound of InfoNCE. Our algorithm EMC^2 improves upon the baselines on small batch size training."
        figures:
          - src: "uploads/emc2_stl10_subset.svg"
            alt: "EMC2 STL10 Subset"
          - src: "uploads/emc2_stl10_subset_grad.svg"
            alt: "EMC2 STL10 Subset Grad"
        caption: "EMC^2 shows fast convergence on the global contrastive loss using a batch size of 4 samples per step, training ResNet-18 on STL-10 subset with SGD."
      - title: "A Two-timescale Primal-dual Algorithm for Decentralized Optimization with Compression"
        class: "dist-opt"
        link: "https://www1.se.cuhk.edu.hk/~htwai/pdf/icassp25-ticopd.pdf"
        year: "2024"
        authors: "Haoming Liu, Chung-Yiu Yau, Hoi-To Wai"
        summary: "tldr: We propose a compressed decentralized optimization that utilize contractive compressor and the primal-dual framework, and analyze its convergence when using exact gradient on nonconvex objective functions."
      - title: "Fully Stochastic Distributed Convex Optimization on Time-Varying Graph with Compression"
        class: "dist-opt"
        link: "https://css.paperplaza.net/images/temp/CDC/files/1088.pdf"
        year: "2023"
        authors: "Chung-Yiu Yau, Hoi-To Wai"
        summary: "tldr: A decentralized optimization algorithm that supports time-varying graph, communication compression and asynchronous local updates. This algorithm is constructed from a primal-dual framework and closely connected to the class of gradient tracking algorithms."
      - title: "Network Effects in Performative Prediction Games"
        class: "dist-opt"
        link: "https://proceedings.mlr.press/v202/wang23ap/wang23ap.pdf"
        year: "2023"
        authors: "Xiaolu Wang, Chung-Yiu Yau, Hoi-To Wai"
        summary: "tldr: We study the existence of equilibrium solutions in a networked performative prediction game, with performative distribution shift on one graph and cooperative aggregation on another graph."
      - title: "DoCoM: Compressed Decentralized Optimization with Near-Optimal Sample Complexity"
        class: "dist-opt"
        link: "https://openreview.net/notes/edits/attachment?id=xQD8RpwrJ6&name=pdf"
        year: "2023"
        authors: "Chung-Yiu Yau, Hoi-To Wai"
        code: "https://github.com/OscarYau525/docom"
        video: "https://www.youtube.com/watch?v=3ZNmkE9ryEs"
        slides: "uploads/DoCoM_slides.pdf"
        summary: "tldr: DoCoM is a decentralized optmization algorithm based on gradient tracking while supports communication compression such as sparsification and quantization. DoCoM incorporates a variance-reduced gradient tracker and speeds-up the non-convex stochastic optimization convergence to the rate of mathcal{O}(T^{-2/3}))."
      - title: "Distributed Optimization for Overparameterized Problems: Achieving Optimal Dimension Independent Communication Complexity"
        class: "dist-opt"
        link: "https://proceedings.neurips.cc/paper_files/paper/2022/file/28795419a644f41ede3fa058b13fc622-Paper-Conference.pdf"
        year: "2022"
        authors: "Bingqing Song, Ioannis Tsaknakis, Chung-Yiu Yau, Hoi-To Wai, Mingyi Hong"
        summary: "tldr: An analysis to the lower bound on communication cost of distributed optimization for optimizing overparameterized problem and a class of algorithms with matching upper bound in terms of model dimension. "
      - title: "Multi-agent Performative Prediction with Greedy Deployment and Consensus Seeking Agents"
        class: "dist-opt"
        link: "https://proceedings.neurips.cc/paper_files/paper/2022/file/fad7c708dda11f3e72cc1629bb130379-Paper-Conference.pdf"
        year: "2022"
        authors: "Qiang Li, Chung-Yiu Yau, Hoi-To Wai"
        summary: "tldr: We study the performative prediction problem on a networked setting, where learner's data distribution has local distribution shift while multiple learners on the network seek a consensal solution."
      - title: "DAP-BERT: Differentiable Architecture Pruning of BERT"
        link: "uploads/DAP_BERT.pdf"
        year: "2021"
        authors: "Chung-Yiu Yau, Haoli Bai, Irwin King, Michael R Lyu"
        code: "https://github.com/OscarYau525/DAP-BERT"
        summary: "tldr: A model pruning method for BERT by optimizing a knowledge distillation objective."
---
