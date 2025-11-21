# 🌊 Styx

[](https://www.google.com/search?q=LICENSE)
[](https://www.python.org/)
[](https://github.com/astral-sh/uv)

**Styx** 是一个基于 Python 的高性能量子多体物理模拟框架。

它的核心愿景是建立一座桥梁，连接**张量网络 (Tensor Networks)** 的确定性收缩方法与 **量子蒙特卡洛 (Quantum Monte Carlo)** 的随机采样技术，为解决强关联量子系统提供灵活、高效的计算工具。

> "Like the river Styx connecting two worlds, this tool connects Tensor Networks and Monte Carlo methods."

## ✨ 特性 (Features)

  * **纯 Python 极简架构**：利用现代 Python 语法构建，易于扩展和调试。
  * **高性能后端**：基于 NumPy 进行密集计算优化（未来计划支持 JAX/Numba）。
  * **混合算法支持**：不仅支持传统的 DMRG/MPS，还致力于探索 TN 与 QMC 结合的前沿算法。
  * **现代工程化**：使用 `uv` 进行依赖管理，类型安全，测试覆盖。

## 🛠️ 安装 (Installation)

本项目使用 [uv](https://github.com/astral-sh/uv) 进行现代化的 Python 环境管理。

### 开发者模式 (推荐)

```bash
# 1. 克隆仓库
git clone https://github.com/YourUsername/Styx.git
cd Styx

# 2. 同步环境 (自动安装 Python 3.14/3.13 和依赖)
uv sync

# 3. 运行示例
uv run examples/simple_mps.py
```

## 🚀 快速开始 (Quick Start)

*(以下为 API 设计预览，随开发进度更新)*

```python
import styx
from styx.tn import MPS

# 初始化一个随机的矩阵乘积态 (MPS)
psi = MPS.random(length=10, bond_dim=16, physical_dim=2)

# 定义哈密顿量 (例如一维海森堡模型)
H = styx.models.Heisenberg1D(length=10, J=1.0)

# 运行 DMRG 寻找基态
energy, ground_state = styx.algorithms.dmrg(psi, H, max_sweeps=5)

print(f"Ground State Energy: {energy:.6f}")
```

## 🗺️ 路线图 (Roadmap)

Styx 的开发分为四个主要阶段。目前的开发重点在于 **Phase 1**。

### Phase 1: 张量网络基础 (Tensor Network Foundations)

构建核心数据结构与一维量子格点算法。

  - [ ] **基础张量封装**：实现支持自动微分和元数据管理的 Tensor 类。
  - [ ] **MPS/MPO 架构**：实现矩阵乘积态 (MPS) 和矩阵乘积算符 (MPO) 的基本操作（正则化、截断）。
  - [ ] **DMRG 实现**：实现密度矩阵重整化群算法，用于基态搜索。
  - [ ] **TEBD 实现**：实现时间演化块抽取算法，用于模拟量子动力学演化。

### Phase 2: 高级收缩引擎 (Advanced Contraction Engine)

优化张量网络的计算效率，处理复杂网络拓扑。

  - [ ] **自定义路径收缩**：允许用户手动指定张量收缩的顺序 (类似于 `einsum`)。
  - [ ] **最优路径搜索**：集成或实现算法（如贪心算法、KaHyPar），自动寻找计算代价最小的收缩路径。
  - [ ] **稀疏性利用**：针对稀疏张量的存储和计算优化。

### Phase 3: 量子蒙特卡洛基础 (QMC Basics)

引入随机算法以处理更大规模的希尔伯特空间。

  - [ ] **VMC 框架**：实现变分蒙特卡洛的基本架构。
  - [ ] **采样算法**：实现 Metropolis-Hastings 算法及局部/全局更新策略。
  - [ ] **可观测量计算**：基于统计样本计算能量、磁化强度、关联函数等物理量。

### Phase 4: 混合算法 (Hybrid TN + QMC)

探索张量网络与蒙特卡洛的结合点（Styx 的核心目标）。

  - [ ] **MPS 采样**：实现从 MPS 波函数中进行高效 Perfect Sampling。
  - [ ] **TN-QMC**：使用张量网络作为变分波函数（Ansatz）进行蒙特卡洛优化。
  - [ ] **PEPS + MC**：针对二维张量网络（PEPS），利用蒙特卡洛方法处理收缩困难问题。

## 🤝 贡献 (Contributing)

欢迎任何形式的贡献！无论是提交 Issue、修复 Bug 还是提交新的算法实现。

1.  Fork 本仓库
2.  创建你的特性分支 (`git checkout -b feature/AmazingFeature`)
3.  提交更改 (`git commit -m 'Add some AmazingFeature'`)
4.  推送到分支 (`git push origin feature/AmazingFeature`)
5.  提交 Pull Request

## 📄 许可证 (License)

本项目基于 MIT 许可证开源 - 详见 [LICENSE](https://www.google.com/search?q=LICENSE) 文件。

-----