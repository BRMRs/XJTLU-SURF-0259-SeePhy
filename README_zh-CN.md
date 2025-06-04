<p align="center">
  简体中文
  ｜
  <a href="https://github.com/BRMRs/XJTLU-SURF-0259-SeePhy/main/README.md">English</a>
</p>


# 项目文档  

## 目录  
1. [简介](#简介)  
2. [项目结构](#项目结构)  
3. [团队成员 Git 基础操作](#团队成员git基础操作)  
4. [提交信息规范](#提交信息规范)  
5. [项目贡献流程](#项目贡献流程)  


## 简介  
本项目致力于提升模型面对复杂带图/带表达式物理题的表现力 
比赛网址: [点此](https://www.codabench.org/competitions/7925/)

## 项目结构  
以下是项目主要文件和文件夹的详细说明：  

```  
project - root/  
├── images/            # 存储 2000 道物理题对应的图片  
├── README.md          # 本说明文档（提供中英文版本）  
├── dev.json           # 用于微调的基础数据，包含 200 个带答案的开发数据样本  
├── example.py         # （如有需要）用于演示的 Python 示例脚本  
├── mini.json          # 包含 200 道题的原始题目数据  
├── public_prediction_example.json # 最终预测提交时期望的答案格式模板  
└── total.json         # 包含 2000 道题的原始题目数据  
```  

### 文件详情  

#### 1. `images/` 文件夹  
- 存储 **2000 道物理题对应的图片**。这些视觉素材对于理解和解决问题（尤其是涉及电路图、坐标系等图表的题目）至关重要。  


#### 2. `dev.json`  
- **用途**：作为模型微调的基础数据。  
- **内容**：包含 200 个带答案的开发数据样本，官方描述为：*"we have provided 200 dev data samples with answers"*。  
- **格式**：  
  ```json  
  {  
      "index": None,  
      "question": "",           # 物理题的文本内容  
      "subject": "",            # 题目类型（如 CM 表示经典力学，OPT 表示光学）  
      "image_path": [           # 与题目相关的图片路径列表  
          
      ],  
      "img_category": "",       # 图表类型（如电路图、坐标系等）  
      "vision_relevance": "",   # 表示图片是否包含解题所需的必要信息  
      "language": "",           # 题目语言（英语/中文）  
      "level": None,            # 所需知识水平  
      "sig_figs": "",           # 答案的有效数字位数  
      "caption": "",            # 图片的文字描述  
      "reasoning": "",          # 解题的推理步骤  
      "answer": ""              # 正确答案  
  }  
  ```  


#### 3. `mini.json` 和 `total.json`  
- **用途**：存储原始物理题目数据。  
  - `mini.json`：包含 **200 道题**的数据。  
  - `total.json`：包含 **2000 道题**的完整数据集。  
- **格式**：  
  ```json  
  {  
      "index": None,  
      "question": "",           # 物理题的文本内容  
      "subject": "",            # 题目类型（如 CM、OPT 等）  
      "image_path": [           # 与题目相关的图片路径列表  
          
      ],  
      "img_category": "",       # 图表类型（如电路图等）  
      "vision_relevance": "",   # 表示图片是否包含解题所需的必要信息  
      "language": "",           # 题目语言（英语/中文）  
      "level": None,            # 所需知识水平  
      "sig_figs": "",           # 答案的有效数字位数  
      "caption": ""             # 图片的文字描述  
  }  
  ```  


#### 4. `public_prediction_example.json`  
- **用途**：作为最终预测提交的模板，这是我们期望的解题答案提交格式。  
- **格式**：  
  ```json  
  {  
      "question": "",           # 物理题的文本内容  
      "subject": "",            # 题目类型（如 CM、OPT 等）  
      "image_path": [           # 与题目相关的图片路径列表  
          
      ],  
      "sig_figs": "",           # 答案的有效数字位数  
      "level": None,            # 所需知识水平  
      "language": "",           # 题目语言（英语/中文）  
      "index": None,            # 题目编号  
      "img_category": "",       # 图表类型（如电路图等）  
      "vision_relevance": "",   # 表示图片是否包含解题所需的必要信息  
      "caption": "",            # 图片的文字描述  
      "prediction": "<think>\n<think>\n\n<think>\n<think>"  # 你的预测解答（遵循思考和答案块结构）  
  }  
  ```  

#### 5. 预测比对规则  
根据主办方的解释（参考项目沟通中的讨论）：  
- 我们主要比对预测中的 **思考和答案块**。  
- 如果结果中不包含此类块，则会比对整个响应内容。  


## 团队成员 Git 基础操作  
如果你刚接触 Git，别担心！以下是贡献项目的简单工作流程：  

### 1. 克隆仓库  
首先，将项目下载到你的电脑：  
```bash  
git clone <仓库地址>  
cd <项目文件夹>  
```  

### 2. 创建新分支  
始终在新分支上工作（切勿直接在 `main` 分支操作）：  
```bash  
git checkout -b <你的分支名称>  
# 示例：git checkout -b feature/添加新数据  
```  

### 3. 进行修改  
使用你喜欢的编辑器编辑文件（如更新数据、修复问题等）。  

### 4. 保存并提交更改  
- 查看已更改的文件：  
  ```bash  
  git status  
  ```  
- 暂存更改：  
  ```bash  
  git add .  # 添加所有更改的文件  
  # 或：git add <特定文件>  
  ```  
- 使用有意义的信息提交（遵循我们的 [提交规范](#提交信息规范)）：  
  ```bash  
  git commit -m "Prefix: Brief description of your changes"  
  ```  

### 5. 推送到远程仓库  
将你的分支上传到 GitHub：  
```bash  
git push origin <你的分支名称>  
```  

### 6. 创建拉取请求（PR）  
- 在浏览器中进入 GitHub 仓库。  
- 为你的分支点击 “Compare & pull request”。  
- 描述你的更改内容，然后提交 PR 以供审核。  


## 提交信息规范  
为了保持项目整洁，所有提交信息必须遵循以下格式：  

```  
Prefix: Short description of the changes (50 characters or less)
```  

### 必需前缀  

- **`[ADD]`** : 添加新文件、数据或功能时使用。
  Example: `[ADD] Add README.md for project documentation`

- **`[UPDATE]`** : 修改现有文件时使用（如更新 `dev.json` 中的数据 ）。    
  Example: `[UPDATE] Update installation instructions in README`

- **`[FIX]`** : 修复错误时使用（如格式问题、链接损坏等 ）。
  Example: `[FIX] Fix typo in main.js`

- **`[DOCS]`** : 更新文档（如本 README ）时使用。
  Example: `[DOCS] Add API documentation for new endpoint`

- **`[STYLE]`** : 规范代码格式
  Example: `[STYLE] Format code with Prettier`


## 项目贡献流程  
1. **在分支上工作**：切勿直接向 `main` 分支提交。使用功能分支（如 `feature/你的任务` ）。  
2. **测试更改**：确保你的更改不会破坏现有功能（如检查 JSON 格式 ）。  
3. **遵循提交规范**：使用必需的前缀，保持提交历史清晰。  
4. **创建清晰的 PR**：在拉取请求中说明你做了哪些更改以及原因。  
