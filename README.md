# paper-list
### Adapter Merging with Centroid Prototype Mapping for Scalable Class-Incremental Learning
code-link:  https://github.com/tf63/ACMap

CVPR 2025

summary: 

训练新任务 -> 得到临时adapter。 

合并 -> 将临时adapter平均融入全局adapter（利用初始权重替换保证合并质量）。

校准 -> 利用新任务在原/新模型下的表现，推算出特征空间的“位移量”，并把这个位移量加到所有旧类别的原型上（质心映射）。

推理 -> 使用唯一的全局模型 + 修正后的原型库进行分类。
### MagMax: Leveraging Model Merging for Seamless Continual Learning
code-link:  https://github.com/danielm1405/magmax

ECCV 2024

summary: 

训练：按顺序一个接一个地微调模型（继承前一个任务的权重）。

计算：计算每个阶段相对于初始模型的差异（任务向量）。

选择：对于每个参数，谁的变化幅度大就听谁的。

合并：将选出的差异加回初始模型，得到最终模型。

优势：MagMax 不仅适用于数据类型毫不相关的任务，更擅长处理数据类型相似、分布相近的任务（如类增量学习），它的核心优势正是在于通过顺序微调减少了相似任务间的参数冲突。
### External Knowledge Injection for CLIP-Based Class-Incremental Learning
code-link:  https://github.com/LAMDA-CL/ICCV25-ENGINE

ICCV 2025

summary: 

输入：新类别数据 + 旧类别原型。

模型前向：

图像 → 冻结视觉编码器 → 视觉注入单元 (损失为原数据和增强后的数据的差异)。

文本 → 冻结文本编码器 → 文本注入单元 (损失为原文本和GPT生成的描述之间的差异)。

损失优化：图文对比损失（基础） + 视觉自监督损失（图像） + 旧原型回放损失（文本）。

推理输出：初步预测得出top-k个候选类别 → 在top-k个候选类别中，GPT-4 生成判别特征（这里有一定权重） → 综合初步预测和GPT-4的判别特征，最终校准结果。
### DC-Merge: Improving Model Merging with Directional Consistency
code-link:  https://github.com/Tobeginwith/DC-Merge

CVPR 2026

summary:

1 计算任务向量
Δi = Wi − W0

2 SVD分解
Δi = Ui Σi Vi^T

3 Energy smoothing
平滑奇异值

4 构造cover space
拼接所有Ui,Vi

5 Whitening
得到 U~, V~

6 投影任务
Mi = U~^T Δi V~

7 合并任务
M~ = merge(Mi)

8 投影回参数空间
Δ~ = U~ M~ V~^T

9 得到最终模型
W~ = W0 + Δ~
