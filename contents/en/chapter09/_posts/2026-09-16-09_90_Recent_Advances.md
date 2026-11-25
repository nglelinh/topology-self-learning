---
layout: post
title: "Lecture 09.90: Recent Advances (2022–2026) — Materials, Neuroscience, Graphs, and Popular TDA"
lang: en
lang-ref: lecture-09-90
chapter: 9
lecture: 90
order: 90
lesson_type: optional
categories: [chapter09]
tags: [optional, recent-advances, materials, neuroscience, graph-tda, applications]
description: "Optional notes: popular topology meets 2022–2026 TDA applications (materials, brain, graphs, NLP). Not a rewrite of the stories."
---

In 1736, Leonhard Euler stood over a map of Königsberg's seven bridges and realized that geography didn't matter—only how vertices and edges connect. Fourteen years later, he wrote down $$V - E + F = 2$$ for convex polyhedra. Nearly three centuries on, those very same ideas are no longer charming puzzle-book anecdotes: in 2022–2026 laboratories, direction-aware Euler characteristic curves predict the elastic stiffness of porous metamaterials, persistent $$H_1$$ loops decode scale-invariant rhythms in human brain connectomes, and Mapper graphs chart semantic neighborhoods across entire corpora of language and video games!

**Optional notes.** The coffee–doughnut, Königsberg, Möbius, Euler, four-colour, DNA, physics, and Poincaré stories stay as they are. We add *where* they now run in applied 2022–2026 papers. The theory / popular-science track is in Vietnamese; this English page holds recent-advance notes only.

---

## Key ideas: From Euler's Formula to Materials, Brain Networks, and NLP

How do Chapter 09's classic visual stories translate into quantitative lab measurements? Three mathematical bridges do the heavy lifting:

1. **Euler Characteristic ($$\chi = V - E + F = \sum_k (-1)^k \beta_k$$):** The single most portable topological invariant in science—computed simply by counting vertices, edges, and faces, yet guaranteed to equal the alternating sum of Betti numbers (components minus loops plus cavities)!
2. **Direction-Aware Topological Descriptors (Euler Characteristic Transform):** A static Betti number forgets *which way* a pore or fiber points. Sweeping a plane across a 3D porous material along every unit direction $$v \in S^2$$ and recording the curve $$t \mapsto \chi(\{x \in K : x \cdot v \le t\})$$ captures both topology *and* anisotropic geometry—enough to predict full mechanical stiffness tensors (Topolnicki et al., 2026)!
3. **Cycle Space ($$\beta_1$$) in Connectomes and Language Graphs:** For any connected graph (no 2-faces), Euler's formula simplifies to $$\beta_1 = E - V + 1$$—counting independent feedback loops. Tracking how $$\beta_0$$ and $$\beta_1$$ evolve as edge-weight thresholds sweep across a brain network or word co-occurrence graph reveals higher-order structure invisible to simple node-degree counts.

---

## 📖 Overview

Chapter 09 teaches topology by pictures. Groups in 2022–2026 do the symmetric thing: take those pictures — holes, knots, networks, surfaces — and measure them on porous materials, biological neural nets, social graphs, and language. This page is a reading map, not a new physics or biology lecture.

![Brain network](https://upload.wikimedia.org/wikipedia/commons/0/0e/Brain_network.png)
*A brain network: a graph whose holes and scales TDA reads. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Brain_network.png)*

![Graph](https://upload.wikimedia.org/wikipedia/commons/3/3d/Undirected_graph.svg)
*An undirected graph: a direct descendant of the seven bridges. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Undirected_graph.svg)*

---

## 🎯 Intuition

Euler’s $V-E+F$ counts the “holes” of a polyhedron. Persistent homology counts the holes of a graph or an atomic cloud *across scales*. No new formula is required: a filtration is. That is why Chapter 09 and Chapter 07 meet in the lab.

### Worked Example (Step by Step): Hand-Checking Euler Characteristic $$\chi$$ on a Cube, a Torus Grid, and a 6-Node Connectome

Verify the exact link $$\chi = V - E + F = \beta_0 - \beta_1 + \beta_2$$ across three concrete structures:

| Structure | Cell counts ($$V, E, F$$) | $$\chi = V - E + F$$ | Betti numbers ($$\beta_0, \beta_1, \beta_2$$) | Alternating sum $$\beta_0 - \beta_1 + \beta_2$$ |
|---|---|---|---|---|
| **Hollow cube ($$S^2$$)** | $$V=8,\ E=12,\ F=6$$ | $$8 - 12 + 6 = \mathbf{2}$$ | $$(1,\ 0,\ 1)$$ | $$1 - 0 + 1 = \mathbf{2}$$ |
| **$$3\times 3$$ periodic torus grid ($$T^2$$)** | $$V=9,\ E=18,\ F=9$$ | $$9 - 18 + 9 = \mathbf{0}$$ | $$(1,\ 2,\ 1)$$ | $$1 - 2 + 1 = \mathbf{0}$$ |
| **Connected 6-node brain graph** | $$V=6,\ E=8,\ F=0$$ | $$6 - 8 + 0 = \mathbf{-2}$$ | $$(1,\ 3,\ 0)$$ | $$1 - 3 + 0 = \mathbf{-2}$$ |

Look at that third row (a connected 6-node, 8-edge brain subnetwork):
- Because a spanning tree on $$V = 6$$ nodes uses exactly $$V - 1 = 5$$ edges, the remaining $$8 - 5 = \mathbf{3}$$ edges must close **3 independent feedback loops** ($$\beta_1 = E - V + 1 = 3$$).
- Compare this to a 6-node, 8-edge network broken into **2** disconnected components ($$C = 2$$): now $$\beta_1 = E - V + C = 8 - 6 + 2 = \mathbf{4}$$ loops! Same vertex count, same edge count, yet different global topology—immediately visible to $$H_0, H_1$$.

### Explanation: How Euler's 1750 Formula Became a 2026 Scientific Instrument

1. **Start with a single invariant number ($$\chi$$):** counting vertices, edges, and faces is blazingly fast—$$O(\text{size})$$—and invariant under any subdivision or rubber-sheet deformation.
2. **Add a filtration to turn a number into a curve:** sweeping a scale threshold (correlation strength in a connectome, or height $$x\cdot v$$ in a 3D porous scan) transforms $$\chi$$ into an **Euler Characteristic Curve** that tracks when pores open and close.
3. **Sweep over directions to recover anisotropic physics:** a porous foam with vertical tunnels is stiffer vertically than horizontally; direction-aware topological descriptors record $$\chi$$ curves along dozens of angles to predict directional stiffness tensors.
4. **Move from passive features to trainable architectures:** once topological summaries prove predictive in materials, neuroscience, and NLP, **Topological Deep Learning (TDL)** bakes those exact complexes directly into neural network layers.

**Quick check.** If you puncture a single square face out of the hollow cube ($$V=8, E=12, F=5$$), what happens to $$\chi$$? It drops from $$2$$ to $$8 - 12 + 5 = \mathbf{1}$$—matching a flat disk ($$\beta_0=1, \beta_1=0, \beta_2=0$$) because opening one face flattens a sphere into a disk!

---

## 📐 Four concrete advances

### 1. Materials and molecules: holes as physical features

Wee and Jiang (2025) survey TDA/TDL in the molecular sciences — where the DNA-knot story (09.06) meets computational chemistry. Topolnicki, Bogdan, Malinowski, Naskręcki, and Harańczyk (2026) use direction-aware topological descriptors to predict stiffness tensors of porous materials: “holes” are no longer a metaphor, they are elastic-model input.

- JunJie Wee, Jian Jiang, *A review of topological data analysis and topological deep learning in molecular sciences*, arXiv:2509.16877 (2025).
- Rafał Topolnicki et al., *Direction-aware topological descriptors for elastic stiffness tensor prediction in porous materials*, arXiv:2604.08105 (2026).

### 2. Neuroscience: networks, scale, and signal

Gisolf, Santos, and Wierstra (2023/24) use persistent homology to separate “signal / noise” from scale invariance in neural and financial networks. A connectome is a huge graph — Königsberg rewritten. Ballester–Casacuberta–Escalera (2023) add how TDA reads *artificial* nets, giving a brain / machine pair.

- Roel Gisolf, Fernando A. N. Santos, Felix Wierstra, *Beyond Signal and Noise: Unraveling Scale Invariance in Neuroscience and Financial Networks with TDA*, arXiv:2311.17912 (2023).
- Rubén Ballester, Carles Casacuberta, Sergio Escalera, *TDA for Neural Network Analysis*, arXiv:2312.05840 (2023).

### 3. TDA on graphs and on language

Uchendu and Le (2024/26) survey TDA in NLP: sentences and corpora become graphs or semantic point clouds, then $H_0,H_1$ are measured. Grelier, Kaufmann, and Pfau (2026) draw Games Mapper — Mapper on Steam genres — a popular-science application in the spirit of Chapter 09.

- Adaku Uchendu, Thai Le, *Topological Data Analysis Applications in Natural Language Processing: A Survey*, arXiv:2411.10298 (2024).
- Nicolas Grelier, Stéphane Kaufmann, Johannes Pfau, *Games Mapper: Topological Data Analysis of Steam Genres*, arXiv:2606.14376 (2026).

### 4. TDL’s place: from story to architecture

Papamarkou et al. (2024) and Su et al. (2025) put the applications into a programme: learn on complexes, not only on graphs. For a Chapter 09 reader the message is simple — the coffee cup and the doughnut are now an *inductive bias* of a layer.

- Theodore Papamarkou et al., *Position: Topological Deep Learning is the New Frontier for Relational Learning*, ICML 2024, arXiv:2402.08871.
- Zhe Su et al., *TDA and TDL Beyond Persistent Homology — A Review*, arXiv:2507.19504 (2025).

---

## 🧠 Papers and references

- Adams & Franzosa, *Introduction to Topology: Pure and Applied* (applied chapters).
- Poincaré, *Analysis Situs* (1895) — the original hole story.
- The arXiv items above.

## 🔗 Applications

A porous-materials lab can replace “stare at an SEM image and guess stiffness” by a direction-aware barcode of the void — Euler characteristic, one direction at a time. That is Lecture 09.04 running on an elasticity tensor.

## Video tham khảo

- **xem trước** [Henry Adams: An Introduction to Applied Topology](https://www.youtube.com/watch?v=Xv4IoKVdGKA) — Kaleidoscope Circles, English. Henry Adams introduces applied topology, the common frame for the materials, signals, and data in this note.
- [An introduction to persistent homology](https://www.youtube.com/watch?v=UxEH7WySO60) — Applied Algebraic Topology Network, English. Persistent homology: holes become measurable features, the point of the materials and signal items.
- [Introduction to Topological Deep Learning](https://www.youtube.com/watch?v=N67GABKImZA) — Mathilde Papillon, English. From the TDA story to an architecture one can train, the topological deep learning item.

## 🧩 Exercises

1. In one sentence, why a connectome needs $H_1$ and not only a vertex/edge count (Königsberg).
2. Take a 6-word sentence, draw a co-occurrence graph, and guess $H_0$.
3. Find in Wee–Jiang (2025) one protein TDA example and retell it in “cup / doughnut / hole” language.
