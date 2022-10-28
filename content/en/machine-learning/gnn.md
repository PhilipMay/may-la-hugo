---
title: Graph Neural Network
---

## Links

### Know-how
- [Learning on Graphs and Geometry Reading Group](https://hannes-stark.com/logag-reading-group)

### Video
- [Stanford CS224W: Machine Learning with Graphs (Jure Leskovec, playlist)](https://www.youtube.com/watch?v=JAB_plj2rbA&list=PLoROMvodv4rPLKxIpqhjhPgdQy7imNkDn)
- [ Stanford Graph Learning Workshop 2022 (7:57 h)](https://www.youtube.com/watch?v=GYW286H3SKw)
- [Petar Veličković](https://www.youtube.com/channel/UC9bkKi8Us7yevvP1KIBQHog/videos)
  - [Everything is Connected: Deep Learning on Graphs](https://www.youtube.com/watch?v=5h6MbQ_65-o)
  - [Theoretical Foundations of Graph Neural Networks](https://www.youtube.com/watch?v=uF53xsT7mjc)
- [Graph Neural Networks](https://www.youtube.com/playlist?list=PLSgGvve8UweGx4_6hhrF3n4wpHf_RV76_)
- [Hussain Kara Fallah](https://www.youtube.com/channel/UCyRGTzxD6Pa4cJOfHmvklQA/videos)
- [Machine Learning TV - not only but also GNN topics](https://www.youtube.com/c/MachineLearningTV/videos)
- [Hannes Stärk](https://www.youtube.com/channel/UC4uWMmEGc5EZVn5pAox-iww/videos)
- [Antonio Longa - PyG tutorials](https://www.youtube.com/user/94longa2112/videos)

### Tools & Libraries
- [PyG (PyTorch Geometric)](https://pytorch-geometric.readthedocs.io/en/latest/) - [GitHub](https://github.com/pyg-team/pytorch_geometric)
  - currentness: well maintained
  - technology: PyTorch
- [GraphGym](https://github.com/snap-stanford/GraphGym) - uses PyG internaly
- [DGL (Deep Graph Library)](https://www.dgl.ai/) - [GitHub](https://github.com/dmlc/dgl/)
  - currentness: well maintained
  - technology: PyTorch, TensorFlow or Apache MXNet
- [Spektral](https://graphneural.network/) - [GitHub](https://github.com/danielegrattarola/spektral/)
  - currentness: maintained
  - technology: Keras & TensorFlow 2
- Graph Nets - [GitHub](https://github.com/deepmind/graph_nets)
  - currentness: outdated, last commit Dec. 2020
  - technology: Tensorflow
  - [arXiv paper](https://arxiv.org/abs/1806.01261)
- [Jraph](https://jraph.readthedocs.io/en/latest/) - [GitHub](https://github.com/deepmind/jraph)
  - currentness: well maintained
  - technology: JAX

### Datasets
- [Open Graph Benchmark (OGB)](https://ogb.stanford.edu/)
- [PyG (PyTorch Geometric) Datasets](https://pytorch-geometric.readthedocs.io/en/latest/modules/datasets.html?highlight=datasets) -
  [Dataset Cheatsheet](https://pytorch-geometric.readthedocs.io/en/latest/notes/data_cheatsheet.html#)
- [TUDatasets](https://chrsmrrs.github.io/datasets/)
- [Benchmarking Graph Neural Networks](https://graphdeeplearning.github.io/post/benchmarking-gnns/) - [GitHub](https://github.com/graphdeeplearning/benchmarking-gnns)

## Recommender Systems at Spotify
- Speaker: Andreas Damianou
- Direct Link: [Stanford Graph Learning Workshop 2022](https://www.youtube.com/watch?v=GYW286H3SKw&t=9537s)

### Papers mentioned
- mentioned at [2:43:40](https://youtu.be/GYW286H3SKw?t=9820)
  - [Grale: Designing Networks for Graph Learning (2020)](https://arxiv.org/pdf/2007.12002.pdf)
- mentioned at [2:57:47](https://youtu.be/GYW286H3SKw?t=10667)
  - Ranking systems for RecSys
    - [Wide & Deep Learning for Recommender Systems (2016)](https://arxiv.org/pdf/1606.07792.pdf)
    - [DCN V2: Improved Deep & Cross Network [...] (2020)](https://arxiv.org/pdf/2008.13535.pdf)
    - [Semi-Supervised Classification with Graph Convolutional Networks (2016)](https://arxiv.org/pdf/1609.02907.pdf)
    - [Deep & Cross Network for Ad Click Predictions (2017)](https://arxiv.org/pdf/1708.05123.pdf)
  - GNN architectures
    - [DeepWalk: Online Learning of Social Representations (2014)](https://arxiv.org/pdf/1403.6652.pdf)
    - [node2vec: Scalable Feature Learning for Networks (2016)](https://arxiv.org/pdf/1607.00653.pdf)
    - [Inductive Representation Learning on Large Graphs (2017)](https://arxiv.org/pdf/1706.02216.pdf)
  - Graph-based appoaches for RecSys
    - [A Survey on Knowledge Graph-Based Recommender Systems (2020)](https://arxiv.org/pdf/2003.00911.pdf)
    - [Graph Learning based Recommender Systems: A Review (2021)](https://arxiv.org/pdf/2105.06339.pdf)
    - [Graph Convolutional Neural Networks for Web-Scale Recommender Systems (2018)](https://arxiv.org/pdf/1806.01973.pdf)
    - [Graph Convolutional Matrix Completion (2017)](https://arxiv.org/pdf/1706.02263.pdf)
    - [Graph Neural Networks for Social Recommendation (2019)](https://arxiv.org/pdf/1902.07243.pdf)
    - [Trajectory Based Podcast Recommendation (2020)](https://arxiv.org/pdf/2009.03859.pdf)
    - [RecWalk: Nearly Uncoupled Random Walks for Top-N Recommendation (2019)](https://dl.acm.org/doi/pdf/10.1145/3289600.3291016)
    - [LightGCN: Simplifying and Powering Graph Convolution Network for Recommendation (2020)](https://arxiv.org/pdf/2002.02126.pdf)
    - [KDD 2022 tutorial by El-Kishky et al.](https://ahelk.github.io/talks/kdd22.html) -
    [slides](https://ahelk.github.io/talks/kdd22/kdd_talk.pdf)
