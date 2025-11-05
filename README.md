# GraphKV: Graph-Based KV Cache Eviction

[![Paper](https://img.shields.io/badge/Paper-EMNLP%202025-blue)](https://arxiv.org/abs/XXXX.XXXXX)
[![License](https://img.shields.io/badge/License-Apache%202.0-green)](LICENSE)

Official implementation of **GraphKV**, a graph-based framework for dynamic KV cache eviction in large language models.

## Abstract
![GraphKV Overview](C:\Users\Cooper\Downloads\OVER.png)
Efficient Key-Value (KV) cache management is essential for processing long text sequences in LLMs. Conventional KV eviction strategies rely on static heuristics that fail to capture evolving token dependencies. GraphKV models tokens as nodes with importance scores and similarity relationships as edges, using a **decay-signal-propagation** mechanism to dynamically update token importance by propagating information across the graph.

## Key Observation

Static importance scoring often retains redundant tokens with high semantic similarity, while discarding moderately important but diverse tokens. GraphKV addresses this by dynamically refining importance scores through similarity-based propagation.

## Contributions

- **Graph Formulation**: KV cache as a graph with tokens as nodes and semantic similarities as edges
- **Decay-Signal-Propagation**: Iteratively propagates decay information to suppress redundant tokens
- **Plug-and-Play**: Compatible with existing KV cache methods (SnapKV, PyramidKV, H2O, etc.)
- **Linear Complexity**: Additional computation is negligible with O(N) complexity

## Experimental Results

### LongBench Performance
- Outperforms suboptimal Knorm by **45.88%**
- Achieves **~3% improvement** over SnapKV and PyramidKV with KV cache size of 512
- Maintains high performance with only **10%** of full KV cache budget

### Needle in a Haystack
- Improves PyramidKV accuracy from **90.3% to 96.9%** (+6.6%)
- Improves SnapKV accuracy from **87.7% to 95.9%** (+8.2%)

## Installation

```bash
git clone https://github.com/EPIC-Lab/GraphKV.git
cd GraphKV
pip install -r requirements.txt
