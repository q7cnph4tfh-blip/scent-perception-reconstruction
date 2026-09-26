[REFERENCES.md](https://github.com/user-attachments/files/32688337/REFERENCES.md)
# References and Scientific Background

本项目是一个独立实现的 **note-level perceptual reconstruction** 原型。

当前公开网页 **不会直接运行** Pyrfume、OpenPOM 或 DREAM 的模型。

这些公开资源主要用于：

- 嗅觉科学背景
- 感知空间设计思路
- 数据组织方式
- mixture perception 的研究参考
- 后续 human sensory validation 设计

---

## 1. Pyrfume

### Project

Pyrfume Public Data Archive

https://github.com/pyrfume/pyrfume-data

Pyrfume 是一个公开嗅觉数据生态，涵盖：

- molecules
- mixtures
- odor descriptors
- behavioral / psychophysical measurements

### 当前项目中的使用方式

**Scientific / data-organization reference only**

当前公开网页没有直接打包或重新分发 Pyrfume 数据集。

注意：即使某个软件仓库采用开放许可证，具体上游数据集仍可能有各自的来源和使用限制，因此后续如果引入数据，需要逐项检查 provenance 与 license。

---

## 2. Principal Odor Map

Lee BK, Mayhew EJ, Sanchez-Lengeling B, et al.

**A Principal Odor Map Unifies Diverse Tasks in Human Olfactory Perception.**

Science. 2023;381:999–1006.

DOI:

https://doi.org/10.1126/science.ade4401

### 与本项目的关系

Principal Odor Map 提供了一个重要思路：

> 气味感知可以用多维 perceptual representation 表达，而不必只归类到单一 fragrance family。

当前项目的手工感知维度并不等同于 Principal Odor Map，也不声称复现其 embedding。

---

## 3. OpenPOM

OpenPOM — Open Principal Odor Map

https://github.com/ARY2260/openpom

OpenPOM 是一个面向 Principal Odor Map 的开源实现 / 复现项目。

### 当前项目中的使用方式

**Methodological reference only**

当前网页：

- 不执行 OpenPOM
- 不读取 SMILES
- 不进行分子级 odor prediction

未来如果能够获得真实化学成分或分子结构信息，才考虑把这一层接入。

---

## 4. DREAM Olfactory Mixtures Prediction Challenge

Official challenge infrastructure:

https://github.com/Sage-Bionetworks-Challenges/olfactory-mixtures-prediction

相关公开研究仓库示例：

https://github.com/Satarifard/DREAM-olfactory-mixtures-prediction-challenge

### 与本项目的关系

DREAM mixture work 对当前项目最重要的启发之一是：

> 多种 odorants 的整体感知不一定等于各成分感知的简单线性相加。

真实混合物中可能出现：

- masking
- suppression
- synergy
- dominance
- emergent odor object

当前版本仍然使用 Top / Heart / Base 的简单线性 baseline，因此 mixture non-linearity 属于后续研究方向。

---

## 5. DREAM 2025 — Odor quality across concentrations and mixtures

Example open-source contribution:

https://github.com/Satarifard/Olfactory-Mixtures-Prediction-2025

相关研究方向包括：

- odor quality across concentration
- multi-component mixture perception
- odor descriptor prediction
- human sensory validation

### 与本项目的关系

未来如果能够获得：

```text
ingredient identity
+
concentration
+
mixture composition
```

就可以进一步探索：

```text
chemical composition
↓
mixture model
↓
predicted perceptual profile
```

当前公开版本还没有进入这一层。

---

# Attribution Policy

## 本项目独立实现的部分

当前公开版本中，以下内容由本项目独立实现：

- Web interface
- fragrance-note input workflow
- perceptual dimensions
- provisional note-level ontology
- Top / Heart / Base weighting baseline
- powderiness dimension
- Texture Tags
- human-readable scent scene rules
- anonymous sensory-feedback workflow

---

## 外部科学参考

当外部项目或论文用于支持以下内容时，会进行引用：

- odor-space representation
- psychophysics
- mixture perception
- human sensory validation
- open-data / reproducibility practices

---

## Third-party code

当前公开网页没有打包或重新分发：

- Pyrfume source code
- OpenPOM source code
- DREAM source code

如果未来实际引入第三方代码，将保留相应：

- copyright
- license
- attribution notices

---

## Third-party data

不会假定：

> 软件仓库的许可证自动覆盖其引用或包含的所有上游数据。

未来若引入外部数据集，会单独检查：

- provenance
- license
- redistribution rights
- citation requirements

---

# Current Project Boundary

当前项目的公开版本主要是：

> fragrance-note semantic reconstruction

而不是：

> chemical odor prediction

因此目前引用这些项目主要用于科学背景、方法设计与后续验证路线，而不是声明“本网页正在运行这些模型”。
