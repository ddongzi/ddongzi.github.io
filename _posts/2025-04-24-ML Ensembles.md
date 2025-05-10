---
title: ML-Ensembles
author: dong
date: 2025-04-24
category: ML
layout: post
---

jupyter对于复制粘贴的图片 不友好，在github ipynb上展示不出来

 

## random forest

[▶️Youtube-random forest](https://youtu.be/J4Wdy0Wc_xQ?si=rvyPCO3CkZoOka-6)  
决策树对训练数据很好，easy to build / use / intercpt, 但是对新测试样本Inaccuracy

<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/8e6cc921-d794-48d6-8e87-d53d3ee3634f.png" alt="图片.png" style="zoom:67%;" />

**Build**

**STEP1**: create a bootstrapped dataset.
randomly choose from original dataset.
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/2c6736de-eda9-4e16-bb10-b10f64834d62.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/34af71c3-45e4-4f7d-8ab9-24a5a052cde5.png" alt="图片.png" style="zoom: 67%;" />

**STEP2** : Create a decision tree using the bootstrapped dataset
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/b13e124c-c886-4f34-9605-af22c11c1330.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/d1f0df52-d59b-4d22-83d6-2cfac0bcc901.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/2ec13046-55b0-4996-ad41-a69f30d35feb.png" alt="图片.png" style="zoom:67%;" />

**Back to STEP 1 and repeat**, we can make many decision trees. This a forest.!

**Use: How to use this forest**:
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/d9de118c-9ff7-49d2-b4b6-bf8dcb3973b0.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/fabe8ab7-e06d-4c5d-8c0e-4e5b9d86ef85.png" alt="图片.png" style="zoom:67%;" />

> **Bagging** : the strategy - plus the vote.

**Estimate :How to know this good ?**: Out-of-Bag Error. (incorrect proportion on outof-bag samples.)
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/2fb6b85b-2b2d-44cc-be1f-446a2020b6a6.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/a938fc43-5dd1-439c-a4b1-2187ff405494.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/cce99413-bed2-44d4-9f40-28b9ee91704a.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/26c33592-3121-4b6e-aa04-1245c7ab51a6.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/e2f93543-3c6c-41a4-8e9d-097c6d41276e.png" alt="图片.png" style="zoom:67%;" />

## Adaboost

[▶️Youtube-Adaboost](https://youtu.be/LsK-xG1cLYA?si=qUL8pOxKBL25niDE)

#### Key view: Stump, Vote weight, order

<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/6bf3feab-6c73-44e2-8d03-ced4cd0caf8c.png" alt="图片.png" style="zoom:67%;" />

**Stump**
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/1eb58afb-8dbc-4d50-982f-4de5eb76d264.png" alt="图片.png" style="zoom:50%;" />

**Vote weight**
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/bec2a67c-54f4-4cf7-809f-95ba69dd5bf5.png" alt="图片.png" style="zoom:67%;" />

**Order**  
Stumps in Adaboost : order is important.Every stump influence how to build next stump.!  
Otherwise, trees in RandomForest is independent







#### Build first stump

<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/23024433-b57b-4315-ae13-06952e008b38.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/0171c3fe-d9ff-4da4-9e7e-8eeb6be299e1.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/623b917a-b26a-4f91-9428-de4ff9905668.png" alt="图片.png" style="zoom:67%;" />
Choose the min Gini index stump as the **first stump** in the forest

> Gini 指数（Gini Index）:衡量节点纯度。 值越小越纯
> $$
> Gini(t) = 1 - \sum_{i=1}^C p_i^2
> $$
>
> - C 是类别总数；
>
> - $p_i$ 是样本中属于第 $i$ 类的比例。
>   假设某个节点包含两个类别，正类和负类，正类占 70%，负类占 30%：
>   $$
>   Gini = 1 - (0.7^2 + 0.3^2) = 1 - (0.49 + 0.09) = 0.42
>   $$
>   



#### Update sample weight : Amount of say

<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/77a88137-62c8-429d-b4a7-ffcaace53041.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/916bc221-7a50-473e-a2fb-a525a053cceb.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/e8f46d6f-3fca-45d1-8488-c42694f01e5d.png" alt="图片.png" style="zoom:67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/5b819619-68f1-4a42-8722-6db0310ab163.png" alt="图片.png" style="zoom:67%;" />
Total Error = sum incorrect sample weight!

**Increase incorrect sample Weight**
![图片.png](https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/9d1eb55c-b129-4eb4-85a5-987ca6bb4dd7.png)
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/788dd7f4-4cd0-4588-801d-0dda0b71a98c.png" alt="图片.png" style="zoom:80%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/bf560c2e-d786-484a-8c30-b1a484b36178.png" alt="图片.png" style="zoom:80%;" />

**Decrease correct sample weight!**
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/8085cb97-8900-4d0d-9107-16535f9e1b64.png" alt="图片.png" style="zoom:80%;" />
![图片.png](https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/8caeb828-78c9-4b5e-ad7d-1e9902166367.png)

**Normalize sample weight**
![图片.png](https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/0ae09a99-6881-4ced-a985-828516ed644d.png)
![图片.png](https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/70bed32f-733d-4699-a465-d9d4bbb965e0.png)

#### Build next stump:


**Method1 - If We have weighted Gini Function**  
We use original dataset with the new sample weight.  
Big sample weight will get bigger gini-index!?

**Method2 - don't**  
Use original dataset with the new sample weight to make a new dataset, than same every sample weight.

轮盘赌创建一个 新dataset

<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/e82750de-405d-4e3e-8d53-7379da5e1b90.png" alt="图片.png" style="zoom: 67%;" />
<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/015fcfb8-56ac-4bbc-ae95-e42b9060539b.png" alt="图片.png" style="zoom:67%;" />

#### How to use

<img src="https://raw.githubusercontent.com/ddongzi/ddongzi.github.io/master/assets/images/2c650de9-5d5d-4c9e-8abe-0b7bb846b4e0.png" alt="图片.png" style="zoom: 67%;" />





## Gradient-Boosted Trees 

迭代构建多个弱学习器（如树），每次纠正之前模型的错误！

### 🌟 1. 基础思想：Boosting

Boosting 是一种 **加法模型** + **前向分步优化** 的策略：

我们希望学得一个函数 $F(x)$，它由多个基模型（通常是树）组成：
$$
F(x) = \sum_{m=1}^{M} \gamma_m h_m(x)
$$


其中：

- $h_m(x)$ 是第 $m$ 个基学习器（比如决策树）；
- $\gamma_m$ 是每个学习器的权重；
- 最终的输出是所有学习器的加权和。

### 📉 2. 梯度提升（Gradient Boosting）

目标是最小化某个损失函数 $L(y, F(x))$，比如平方误差或交叉熵。

由于直接优化很难，我们采用 **前向分步策略**：

第 $m$ 步时，我们固定前面 $m-1$ 步的结果 $F_{m-1}(x)$，让新模型 $h_m(x)$ 去拟合当前模型的负梯度方向：
$$
r_i^{(m)} = - \left[ \frac{\partial L(y_i, F(x_i))}{\partial F(x_i)} \right]_{F = F_{m-1}}
$$


这些 $r_i^{(m)}$ 被称为 **伪残差（pseudo residuals）**。

然后我们训练一棵树 $h_m(x)$ 去拟合这些伪残差。


### 🔄 3. 模型更新

新模型的更新方式是：

$F_m(x) = F_{m-1}(x) + \eta \cdot \gamma_m h_m(x)$

- $\eta \in (0, 1]$ 是学习率（learning rate），控制每次纠正的“步长”；
- $\gamma_m$ 是通过一维搜索确定的最佳系数（最小化当前损失）；
- 加上这一项后，整体模型变得更好。


### 🧠 举个例子（回归，MSE）

1. 初始化：用训练集的均值作为初始预测 $F_0(x)$
2. 第 $m$ 步：
   - 计算残差：$r_i = y_i - F_{m-1}(x_i)$
   - 拟合一棵树：用 $r_i$ 作为目标
   - 得到新树 $h_m(x)$
   - 更新模型：
      $F_m(x) = F_{m-1}(x) + \eta h_m(x)$

这样不断迭代，每一步都在“**纠正**”上一轮的误差.





