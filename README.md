# paper-list
### Adapter Merging with Centroid Prototype Mapping for Scalable Class-Incremental Learning
code-link:  https://github.com/tf63/ACMap

CVPR 2025

summary:  
训练新任务 -> 得到临时adapter。 

合并 -> 将临时adapter平均融入全局adapter（利用初始权重替换保证合并质量）。

校准 -> 利用新任务在原/新模型下的表现，推算出特征空间的“位移量”，并把这个位移量加到所有旧类别的原型上（质心映射）。

推理 -> 使用唯一的全局模型 + 修正后的原型库进行分类。
