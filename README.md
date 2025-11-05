
# GraphKV: Breaking the Static Selection Paradigm with Graph-Based KV Cache Eviction


<div align="center">
<img src="https://github.com/lxlcooper/GraphKV/blob/main/OVER.png" width="500" alt="GraphKV Overview">
</div>


## 📖 Abstract

<div style="font-size: 16px">

Efficient Key-Value (KV) cache management is essential for processing long text sequences in LLMs. Conventional KV eviction strategies rely on static heuristics that fail to capture evolving token dependencies. **GraphKV** models tokens as nodes with importance scores and similarity relationships as edges, using a **decay-signal-propagation** mechanism to dynamically update token importance by propagating information across the graph.

</div>



---

## 🔍 Key Observation

<div align="center">
<img src="https://github.com/lxlcooper/GraphKV/blob/main/Observation.png" width="800" alt="GraphKV Overview">
</div>

<div style="font-size: 16px">

Static importance scoring often retains **redundant tokens** with high semantic similarity, while discarding **moderately important but diverse tokens**. GraphKV addresses this by dynamically refining importance scores through similarity-based propagation.

</div>

<div align="center">
<img src="https://github.com/lxlcooper/GraphKV/blob/main/Method.png" width="800" alt="GraphKV Overview">
</div>

---

## 🎯 Contributions

<div style="font-size: 16px">

- **📊 Graph Formulation**: KV cache as a graph with tokens as nodes and semantic similarities as edges
- **🔄 Decay-Signal-Propagation**: Iteratively propagates decay information to suppress redundant tokens
- **🔌 Plug-and-Play**: Compatible with existing KV cache methods (SnapKV, PyramidKV, H2O, etc.)
- **⚡ Linear Complexity**: Additional computation is negligible with O(N) complexity

</div>

---

## 📈 Experimental Results

### 🏆 LongBench Performance

<div style="font-size: 16px">

- **Outperforms suboptimal Knorm by 45.88%**
- **Achieves ~3% improvement** over SnapKV and PyramidKV with KV cache size of 512
- **Maintains high performance** with only 10% of full KV cache budget

