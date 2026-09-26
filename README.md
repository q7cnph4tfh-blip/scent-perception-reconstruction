[README.md](https://github.com/user-attachments/files/32688345/README.md)
# Scent Perception Reconstruction

一个将香水、香膏或香氛产品的 **前调 / 中调 / 后调** 转换为更直观闻感描述的开源小工具。

在线体验：

https://q7cnph4tfh-blip.github.io/scent-perception-reconstruction/

---

## 这个项目做什么？

很多香氛产品会给出：

- Top Notes / 前调
- Heart Notes / 中调
- Base Notes / 后调

但仅看到“桂花、黄杏、黄葵子、雪松”这样的香调表，仍然很难直接想象：

> 它闻起来到底是什么感觉？

这个项目尝试建立一个简单的桥梁：

```text
Fragrance Notes
        ↓
Perceptual Features
        ↓
Human-readable Scent Impression
```

也就是：

**香调语言 → 感知特征 → 人可以理解的闻感描述**

---

## 当前支持的输出

### 主感知维度

- 明亮感 `brightness`
- 暖感 `warmth`
- 湿润感 `wetness`
- 甜润感 `sweetness`
- 青绿感 `greenness`
- 花香 `floral`
- 果香 `fruity`
- 木质感 `woody`
- 烟熏感 `smoky`
- 麝香 / 肌肤感 `musky`
- 奶油感 `creamy`
- 脂粉感 `powderiness`
- 通透感 `airiness`

### Texture Tags

作为第二层材质 / 意象标签，目前包括：

- 皂感 `soapy`
- 蜡感 `waxy`
- 树脂感 `resinous`
- 药感 `medicinal`
- 酒感 `boozy`

### 其他输出

- 前调 → 中调 → 后调的感知变化
- 第一感受
- 一句话“像什么”的场景描述
- 未收录香调提示
- 真实用户闻感反馈入口

---

## 脂粉感是什么？

本项目把 **Powderiness / 脂粉感** 作为独立维度。

它主要指：

- 化妆粉 / 粉盒式气味联想
- 干爽粉质
- 柔雾感
- 细腻、粉末状的嗅觉质地

它不等同于：

- 甜度
- 奶油感
- 麝香感

一款香可以很甜但不粉，也可以很粉但并不甜。

---

## 当前模型

每个已收录香调会映射到一组 0–1 的 provisional perceptual priors。

当前整体 profile 使用一个简单、可复现的 baseline：

```text
Overall Profile
=
0.30 × Top
+
0.45 × Heart
+
0.25 × Base
```

这个权重只是第一版工程基线，不代表真实香水的挥发动力学。

---

## 当前版本的科学边界

当前模型属于：

### NOTE-LEVEL PERCEPTUAL RECONSTRUCTION

它不是：

- 香水真实化学配方重建
- GC–MS 成分预测
- 单分子气味预测模型
- 真实挥发动力学模拟
- 人体感官实验的替代品

商品页中的“桂花”“琥珀”“麝香”“水生花”等词，可能代表：

- 天然原料
- 单个香料分子
- 多种分子的 accord
- 品牌的香调描述

因此当前版本只在 **香调语义 → 感知表型** 这一层进行重建。

---

## 当前开发集

第一版主要围绕 7 款香膏进行开发与测试。

同时支持用户自行输入其他：

- 香水
- 香膏
- 扩香
- 香氛产品

只要能够提供较明确的：

- 前调
- 中调
- 后调

就可以尝试进行闻感重建。

---

## Human Feedback

网页结果页提供：

> 我闻过实物，匿名提交真实反馈

真实反馈用于比较：

```text
Model Prediction
vs.
Human Perception
```

当前不会因为单个用户反馈立即修改模型。

计划是在积累一定数量真实评价后，再进行批量分析，例如：

- predicted vs observed
- human median
- inter-user disagreement
- systematic over-estimation / under-estimation

然后再更新下一版本。

---

## Privacy

反馈问卷用于匿名模型校准。

网页本身不主动要求：

- 姓名
- 手机号
- 邮箱
- 精确位置
- 其他直接身份信息

也请不要在自由文本反馈中填写个人敏感信息。

---

## 开放与可复现

当前项目希望保持：

- 方法透明
- 参数可解释
- 版本可追踪
- 引用可追溯
- 用户反馈与模型更新分开

后续如果根据真实反馈修改 ontology 或权重，会通过版本记录说明。

---

## Scientific References

本项目的科学设计受到公开嗅觉研究与开源项目启发，包括：

- Pyrfume
- Principal Odor Map
- OpenPOM
- DREAM Olfactory Mixtures Prediction Challenge

详见：

`REFERENCES.md`

---

## Version

Current public prototype:

`v0.7`

---

## Status

```text
Public Web App        ✓
7-product DEV set     ✓
Note ontology         provisional
Texture Tags          ✓
Human feedback        active
Chemical model        not implemented
Mixture ML model      not implemented
Sensory calibration   collecting data
```

---

## Disclaimer

当前结果应理解为：

> an interpretable perceptual estimate based on fragrance-note descriptions

而不是：

> an experimentally verified reconstruction of the actual fragrance formulation

随着真实用户反馈增加，当前 ontology、感知参数和时间权重会逐步校准。
