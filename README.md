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
