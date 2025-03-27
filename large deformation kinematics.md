# 大变形运动学理论

大变形运动学理论的核心在于处理几何非线性问题，即结构的变形显著改变几何形状，导致应力、应变分布和载荷方向的变化。

## 变形梯度张量（Deformation Gradient Tensor）

描述材料点从初始构型到当前构型的变形与旋转，定义为：

$$
F_{ij} = \frac{\partial x_i}{\partial X_j}
$$

其中：

- $X_j$ 为初始坐标（材料坐标）
- $x_i$ 为当前坐标（空间坐标）

变形梯度可分解为旋转张量和右Cauchy-Green张量，分别表征刚体旋转和真实变形。

###### 由于本构方程中经常需要用到二阶张量的主不变量关于该张量本身的导数,以下对此内容进行补充

## 第一不变量 $I_1$

第一不变量 $I_1$ 是张量 $A$ 的迹（Trace），表示为：

$$
I_1(\textbf{\textit{A}}) = \mathrm{tr}(\textbf{\textit{A}}) = A_{kk}
$$

其中：

- $A_{kk}$ 表示张量对角分量的和（Einstein求和约定）

### 偏导数计算

第一不变量对张量分量的偏导数：

$$
\frac{\partial I_1}{\partial A_{ij}} = \frac{\partial A_{kk}}{\partial A_{ij}} = \delta_{ki}\delta_{kj} = \delta_{ij}
$$

式中：

- $\delta_{ij}$ 为Kronecker Delta符号（当$i=j$时为1，否则为0）
- $A_{kk} = A_{11} + A_{22} + A_{33}$ 表示张量的迹
- $\delta_{ki}\delta_{kj}$ 仅在$k=i$且$k=j$时为1（即要求$i=j=k$）

### 张量形式：

$$
\frac{\partial I_1}{\partial \textbf{A}} = \textbf{I}
$$

其中：

- $\dfrac{\partial I_1}{\partial \textbf{A}}$ 表示第一不变量 $I_1$ 对张量分量 $A$ 的导数
- $\textbf{I}$ 表示二阶单位张量（单位矩阵）

## 第二不变量 $I_2$

第二不变量 $I_2$ 表示为：

$$
I_2(\textbf{\textit{A}}) = \frac{1}{2} \left( \text{tr}^2(\textbf{\textit{A}}) - \text{tr}(\textbf{\textit{A}} \cdot \textbf{\textit{A}}) \right) = \frac{1}{2} \left( A_{kk} A_{ll} - A_{kl} A_{lk} \right)
$$

其中：

- $A_{kk}$ 和 $A_{ll}$：张量 $A$ 的迹，即对角分量之和 $(A_{11} + A_{22} + A_{33})$
- $A_{kl} A_{lk}$：张量 $A$ 的平方迹，满足关系：

$$
\text{tr}(A^2) = A_{11}^2 + A_{12}A_{21} + A_{13}A_{31} + A_{21}A_{12} + A_{22}^2 + \cdots + A_{33}^2
$$

## 第二不变量对张量分量的偏导数

主要公式：

$$
\begin{align}
\frac{\partial I_2}{\partial A_{ij}} 
&= \frac{\partial \left( \frac{1}{2} (A_{kk} A_{ii} - A_{ki} A_{ik}) \right)}{\partial A_{ij}} \\
&= \frac{1}{2} \left( \delta_{ki} \delta_{kj} A_{ii} + \delta_{ii} \delta_{ij} A_{kk} - \delta_{ki} \delta_{ij} A_{ik} - \delta_{ii} \delta_{kj} A_{ki} \right) \\
&= A_{kk} \delta_{ij} - A_{ji}
\end{align}
$$

注释项：

- $\delta_{ki}\delta_{kj}A_{ii}$ 项对应：

$$
\frac{\partial (A_{kk} A_{ii})}{\partial A_{ij}} = A_{kk} \delta_{ij} \quad (\text{当 } k=i \text{ 且 } k=j \text{ 时为1，否则为0})
$$

- $\delta_{ki}\delta_{ij}A_{ik}$ 项对应：

$$
\frac{\partial (A_{ki} A_{ik})}{\partial A_{ij}} = A_{ji}
$$

### 张量形式：

$$
\frac{\partial I_2}{\partial \textbf{A}} = I_1 \textbf{I} - \textbf{A}^\top
$$

其中：

- $I_1$：第一不变量，定义为 $I_1 = A_{kk}$（爱因斯坦求和约定）
- $\textbf{I}$：二阶单位张量（单位矩阵），分量为 $\delta_{ij}$
- $\textbf{A}^\top$：张量 $\textbf{A}$ 的转置，分量为 $A_{ji}$

---

## 本构关系与材料模型

### 超弹性模型

#### 可压缩Neo-Hookean model 模型1

在3D中广泛使用的能量密度之一，由以下公式给出：

$$ W = \frac{1}{2} \mu (I_1 - 3) - \mu \ln J + \frac{1}{2} \lambda \Theta(J)^2 $$

-  经典剪切项（第一项）
-  修正项（第二项
-  体积项（第三项）

其中：

- \$\lambda, \mu\$: 拉梅常数，分别对应材料的体积模量和剪切模量
- \$I\_1 = \mathrm{tr}(\mathbf{C})\$；右柯西-格林张量 \$\mathbf{C} = \mathbf{F}^\top \mathbf{F}\$ 的第一不变量（迹）
- \$J = \det \mathbf{F} = \sqrt{\det \mathbf{C}}\$，变形梯度 \$\mathbf{F}\$ 的行列式，表示体积变化率
- \$\Theta(J)\$ 需满足两个条件的平滑函数：
  1. \$\Theta(J) = 0\$ 当且仅当 \$J = 1\$（体积无变化时函数值为零）
  2. \$\Theta'(J) \neq 0\$（函数在 \$J=1\$ 处导数非零）

---

## 经典剪切项 $\frac{1}{2}\mu (I_1 - 3)$

1. 描述材料抵抗形状变化的能力（剪切能），但未分离体积变形的影响
2. 当材料发生纯体积变形（如均匀膨胀）时，$\mathbf{I_1 = \mathrm{tr}(C)}$会随体积变化而增大，导致剪切能错误地包含体积变形贡献

## 修正项 $-\mu \ln J$

消除体积变形对剪切能的耦合，具体过程：

1. 当材料发生纯体积变形$\mathbf{F = J^{1/3}I}$（即等容变形梯度$\mathbf{\bar{F} = I}$），此时：
   $$
   I_1 = \mathrm{tr}(\mathbf{C}) = \mathrm{tr}(\mathbf{F^\top F}) = J^{2/3} \mathrm{tr}(\mathbf{I}) = 3J^{2/3}
   $$
2. 经典剪切项变为$\frac{1}{2}\mu \left( 3J^{2/3} - 3 \right)$仍包含体积变形项$J$
3. 修正项$- \mu \ln J$通过补偿$J^{2/3}$的影响，使得剪切项在纯体积变形时退化为零：
   $$
   \frac{1}{2}\mu \left( 3J^{2/3} - 3 \right) - \mu \ln J \xrightarrow{J\to1} 0
   $$
4. ​**物理意义**：修正项抵消了体积变形对剪切能的"虚假贡献"，实现剪切能与体积变形的解耦

## 体积项 $\frac{1}{2}\lambda\Theta(J)^{2}$

- 直接控制体积变形能
- $\lambda$调节体积刚度
- $\Theta(J)$定义体积变形形式（如线性或对数型）

---

# (2) 可压缩 Neo-Hookean 模型 2

$$
W = \underbrace{\frac{1}{2} \mu \left( J^{-2/3} I_1 - 3 \right)}_{\text{等容剪切项}} 
+ \underbrace{\frac{1}{2} K \left( \frac{1}{2} (J^2 - 1) - \ln J \right)}_{\text{体积项}}
$$

## 等容剪切项 $\frac{1}{2}\mu \left( J^{-2/3}I_1 - 3 \right)$

1. 通过$J^{-2/3}$显式消除体积变形对$I_1$的影响
2. 当材料发生纯体积变形$\mathbf{F = J^{1/3}I}$，此时：
   $$
   I_1 = 3J^{2/3} \Rightarrow \frac{1}{2}\mu \left( J^{-2/3} \cdot 3J^{2/3} - 3 \right) = 0
   $$
3. ​**物理意义**：剪切能仅由形状变化（等容变形）贡献，与体积变形无关

## 体积项

- 仅依赖$J$
- 参数$K$直接控制体积刚度

---

# 2. 变形分解方式的数学推导

## （1）模型1：未显式分离等容与体积变形

- ​**未显式分离**：能量函数中未通过乘式分解将$\mathbf{F}$分解为等容部分和体积部分
- ​**根本原因**：经典剪切项$\frac{1}{2}\mu (I_1 - 3)$中$\mathbf{I_1 = \mathrm{tr}(C)}$包含体积变形影响

### 推导示例：纯体积变形分析

**步骤1：定义纯体积变形下的变形梯度张量**

$$
\mathbf{F} = J^{1/3} \mathbf{I}
$$

**推导依据**：

1. 体积变化率$J = \det(\mathbf{F})$
2. 均匀膨胀时$\mathbf{F}$为各向同性张量,
3. $\det(\mathbf{F}) = \lambda^3 \Rightarrow \lambda = J^{1/3}$

**步骤2：计算右柯西-格林变形张量$C$**

根据定义 $C = F^T F$，代入 $F = J^{1/3}I$：

$$
C = (J^{1/3}I)^T (J^{1/3}I) = J^{1/3}J^{1/3} I^T I = J^{2/3}I
$$

1. $I$ 是单位矩阵，$I^T = I$，且 $I I = I$
   （张量规范：单位矩阵保持正体，转置运算符正确标注）
2. 标量乘法满足交换律，因此 $J^{1/3} J^{1/3} = J^{2/3}$
   （规范修正：标量$J$与张量$I$明确分离，指数采用标准分数形式）

**步骤3：计算第一不变量**

$$
I_1 = \mathrm{tr}(\mathbf{C}) = 3J^{2/3}
$$

**步骤4：经典剪切项表达式**

$$
\frac{1}{2}\mu(3J^{2/3} - 3) = \frac{3}{2}\mu(J^{2/3} - 1)
$$

**总结**

1. 经典剪切项 $\frac{1}{2} \mu (I_1 - 3) - \frac{1}{2} \mu (3J^{2/3} - 3)$ 仍然包含 $J$，表明剪切能与体积变形未解耦。
2. 修正项 $-\mu \ln J$ 的作用是抵消这一耦合。

#### 修正项作用：

**推导：​**

当变形为纯体积变形$( \overline{C}=I)$，剪切项和修正项的总和为：

$$
\frac{1}{2}\mu(3J^{2/3} - 3) - \mu\ln J
$$

展开泰勒级数（$J \longrightarrow 1$）：

$$
\begin{aligned}
3J^{2/3} &\approx 3\left( 1 + \frac{2}{3}(J - 1) \right) + \cdots \\
\ln J &\approx J - 1
\end{aligned}
$$

代入后：

$$
\frac{1}{2}\mu\left(3 + 2(J - 1) - 3\right) - \mu(J - 1) = \mu(J - 1) - \mu(J - 1) = 0
$$

**物理意义：​**
修正项消除了$J$对剪切能的贡献，使剪切能仅由形状变化（$\overline{C} \neq I$）产生。

---

## （2）模型2：显式分离等容与体积变形

- ​**显式分离**：通过乘式分解$\mathbf{F = J^{1/3}\bar{F}}$（$\det\mathbf{\bar{F}} = 1$）
- ​**张量分解**：
  $$
  \mathbf{C} = J^{2/3}\mathbf{\bar{C}},\quad \mathbf{\bar{C}} = \mathbf{\bar{F}^\top\bar{F}}
  $$

$$
\begin{aligned}
W &= \frac{1}{2}μ (J^{-2/3}I_1 - 3) + \text{体积项} \\
  &= \frac{1}{2}μ (\text{tr}(\bar{ \mathbf{C}}) - 3) + \text{体积项}
\end{aligned}
$$

### 推导示例：变形梯度分解

**步骤1：变形梯度张量分解**

$$
\mathbf{F} = J^{1/3}\mathbf{\bar{F}},\quad \det(\mathbf{\bar{F}}) = 1
$$

$$
\begin{aligned}
\det(\mathbf{F}) &= \det\left(J^{1/3} \bar{\mathbf{F}}\right) \\
&= \left(J^{1/3}\right)^3 \det(\mathbf{F}) \\
&= J \cdot \det(\mathbf{\bar{F}})
\end{aligned}
$$

**步骤2：验证等容条件**

**原式：​**

$$
\mathbf{C} = J^{2/3} \bar{ \mathbf{C}}
$$

**推导过程：​**

1. ​**右柯西-格林张量的定义**
   
   $ \mathbf{C} = F^\top F$，将 $F = J^{1/3}\bar{F}$ 代入：
   
   $$
   \mathbf{C} = \left(J^{1/3}\bar{F}\right)^\top \left(J^{1/3}\bar{F}\right) = J^{2/3}\bar{F}^\top \bar{F} = J^{2/3}\bar{ \mathbf{C}}
   $$
2. ​**定义等容右柯西-格林张量**
   
   $\bar{ \mathbf{C}} = \bar{F}^\top \bar{F}$，则：
   
   $$
   \mathbf{C} = J^{2/3}\bar{ \mathbf{C}}
   $$

**步骤3：等容剪切项表达式**

原式:

$$
I_1 = \text{tr}( \mathbf{C})= J^{2/3} \text{tr}(\bar{ \mathbf{C}})
$$

$$
J^{-2/3}I_1=\text{tr}(\bar{ \mathbf{C}})
$$

推导过程：

1. 计算 $I_{1} = \operatorname{tr}( \mathbf{C})$
   
   由 $ \mathbf{C} = J^{2/3}\bar{ \mathbf{C}}$，代入得：
   
   $$
   I_{1} = \operatorname{tr}( \mathbf{C}) = \operatorname{tr}\left(J^{2/3}\bar{ \mathbf{C}}\right) = J^{2/3}\operatorname{tr}(\bar{ \mathbf{C}})
   $$
   
   （标量 $J^{2/3}$ 可提到迹运算外）
2. 解出 $\text{tr}(\bar{ \mathbf{C}})$
   
   将等式两边乘以 $J^{-2/3}$，得：
   
   $$
   J^{-2/3}I_{1}= \text{tr}(\bar{ \mathbf{C}})
   $$

代入

$$
\frac{1}{2}\mu\left(J^{-2/3}I_1 - 3\right) = \frac{1}{2}\mu(\mathrm{tr}(\mathbf{\bar{C}}) - 3)
$$

**物理意义**：

- ​**剪切项**仅依赖等容变形$\bar{ \mathbf{C}}$，与$J$无关。
- ​**体积项**仅依赖$J$，与等容变形无关。

## 可压缩Neo-Hookean model 模型1的PK2应力推导

###### PK2应力（记为S）是材料描述下的应力度量，与参考（未变形）构型相关。其推导基于应变能密度函数对变形的响应。

可以通过以下方式实现PK2应力：

$$
S_{IJ} = 2 \frac{\partial W}{\partial C_{IJ}}
$$

其中：

- $S_{ij}$：第二类Piola-Kirchhoff应力（PK2应力）的分量
- $W$：应变能密度函数（Strain Energy Density Function）
- $C_{IJ}$：右Cauchy-Green变形张量的分量，定义为 $C = F^\top F$

能量密度 $W$ 的表达式包含 $I_1$ 和 $J$，因此需应用链式法则：

$$
S_{IJ}= 2 \left( \frac{\partial W}{\partial I_1} \frac{\partial I_1}{\partial C_{IJ}} + \frac{\partial W}{\partial J} \frac{\partial J}{\partial C_{IJ}} \right)
$$

### 偏导数计算

- 对 $I_1$ 的偏导数：

$$
\frac{\partial W}{\partial I_1} = \frac{1}{2}\mu
$$

- 对 $J$ 的偏导数：

$$
\frac{\partial W}{\partial J} = -\frac{\mu}{J} + \lambda\theta\theta' \quad \text{其中}\ \theta' = \frac{d\theta}{dJ}
$$

### 右柯西-格林张量导数

$$
\frac{\partial I_1}{\partial C_{IJ}} = \delta_{IJ} \\

\frac{\partial J}{\partial C_{IJ}} = \frac{1}{2}J C_{IJ}^{-1}
$$

将上述结果代入链式法则表达式：

$$
S_{IJ} = 2 \left( \frac{1}{2} \mu \delta_{IJ} + \left( \lambda \theta\theta' - \mu \frac{1}{J} \right) \cdot \frac{1}{2} J C_{IJ}^{-1} \right)
$$

简化后得到：

$$
S_{IJ} = \mu \delta_{IJ} + (\lambda \theta\theta' - \mu) C_{IJ}^{-1}
$$

能量密度函数W定义了材料的弹性行为，而PK2应力S通过导数将变形映射到应力，从而建立本构关系。这种框架在有限元分析中广泛应用，特别是在处理超弹性材料（如橡胶、软组织）的大变形问题时。

---

## 常用的大变形材料

1. ​**超弹性材料**
   
   - 典型材料：
     - 橡胶（如天然橡胶、硅橡胶）
     - 聚合物弹性体（如聚氨酯、热塑性弹性体）
   - 特性与模型：
     - 具有高度可逆的非线性变形能力，适用于大应变（100%以上）场景
     - 常用超弹性本构模型包括 Mooney-Rivlin、Neo-Hookean 和 Ogden 模型，用于模拟橡胶密封件、轮胎、软体机器人等
   - 应用场景：
     - 汽车减震器、医疗导管、可穿戴设备的柔性部件
2. ​**金属塑性材料**
   
   - 典型材料：
     - 铝合金（如硬铝、超硬铝合金）
     - 钢（如低碳钢、不锈钢）
     - 钛合金
   - 特性与模型：
     - 在塑性成形（如冲压、锻造）中表现出大应变（>10%）和加工硬化效应
     - 使用 von Mises 屈服准则和各向同性/随动硬化模型模拟金属的延展性变形
   - 应用场景：
     - 航空航天结构件（如飞机蒙皮、发动机叶片）
     - 汽车钣金冲压
     - 金属3D打印
3. ​**岩土与混凝土材料**
   
   - 典型材料：
     - 黏土、砂土
     - 混凝土、岩石
   - 特性与模型：
     - 具有应变软化和剪胀特性，需采用 Drucker-Prager 模型 或 Cam-Clay 模型
     - 大变形分析用于滑坡、地基沉降、隧道开挖等场景
   - 应用场景：
     - 岩土工程中的边坡稳定性分析、地下结构抗震设计
4. ​**复合材料与蜂窝结构**
   
   - 典型材料：
     - 纤维增强复合材料（如碳纤维/环氧树脂）
     - 拉胀蜂窝结构（负泊松比材料）
   - 特性与模型：
     - 通过设计微观结构（如蜂窝、波纹夹层）实现可控的大变形响应
     - 柔性复合材料可通过调节面内泊松比适应复杂变形需求，例如变形机翼蒙皮
   - 应用场景：
     - 航空航天变形结构、可展开卫星天线、柔性电子器件基底
5. ​**生物与软组织材料**
   
   - 典型材料：
     - 生物软组织（如皮肤、血管、肌肉）
     - 水凝胶、仿生材料
   - 特性与模型：
     - 具有粘弹性、超弹性和率相关性，常用 Fung 模型 或准线性粘弹性模型
     - 大变形分析用于手术模拟、假体设计、药物递送系统优化
   - 应用场景：
     - 生物力学仿真、可植入医疗器械开发
