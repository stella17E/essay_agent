# Essay Evaluation Agent

## 🎯 项目定位

An AI-powered essay evaluation agent that automates 70% of low-level error detection, enabling teachers to focus on high-value feedback.

**目标用户**：初中语文教师 / 英文写作教师
**核心价值**：帮助教师节省重复批改的时间，让他们把精力放在高阶点评上。

---

## ✨ 核心功能

* **自动识别文章逻辑缺陷**（如论点缺失、结构松散）
* **区分文体给出评价**：

  * 记叙文：叙事完整性、细节描写、情感表达
  * 议论文：论点完整性、论据支持、逻辑衔接
* **生成结构化反馈报告**（JSON 格式），包括：错误类别、示例句子、修改建议
* **整体评分**，并提供总结性反馈

---

## 🛠 技术实现

* 基于大语言模型（OpenAI GPT 系列）
* **Prompt + 规则引擎**，轻量化实现，无需模型微调
* **FastAPI** 提供后端接口
* 输出结果严格符合 JSON Schema，可直接对接前端展示

### JSON 输出示例

```json
{
  "essay_type": "narrative",
  "dimensions": [
    {
      "name": "叙事完整性",
      "score": 2,
      "issue_examples": ["文章缺少开头的背景交代"],
      "suggestion": "补充背景，引出故事情节"
    },
    {
      "name": "细节描写",
      "score": 3,
      "issue_examples": ["‘他很开心’过于笼统"],
      "suggestion": "增加具体动作或表情描写"
    }
  ],
  "overall_score": 7,
  "general_feedback": "整体结构清晰，但细节和情感描写略显不足。"
}
```

---

## ⚙️ 本地运行

> 需要 Python 3.9+

```bash
git clone https://github.com/<your-username>/essay-evaluation-agent.git
cd essay-evaluation-agent
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows (PowerShell)
# .venv\\Scripts\\Activate.ps1
pip install -r requirements.txt
uvicorn main:app --reload
```

启动后访问：`http://127.0.0.1:8000/docs`（Swagger 界面），可在页面中直接测试 `/evaluate` 接口。

### API 调用示例（curl）

```bash
curl -X POST http://127.0.0.1:8000/evaluate \
  -H "Content-Type: application/json" \
  -d '{
    "essay_type":"narrative",
    "essay_text":"今天我去郊游了，阳光很好，然后……"
  }'
```

---

## 📁 项目结构（建议）

```
.
├── main.py               # FastAPI 入口，/evaluate 接口
├── requirements.txt      # 依赖
├── app/
│   ├── rules.py          # 规则引擎（连接词、句长、标点等）
│   ├── llm.py            # LLM 调用与 Prompt 模板
│   └── schema.py         # JSON Schema 定义
├── examples/
│   ├── inputs/           # 示例作文
│   └── outputs/          # 示例报告（JSON）
└── README.md
```

---

## 📌 评价维度（与产品定义一致）

**记叙文（Narrative）**

* 叙事完整性（起承转合）
* 细节描写（动作/感官细节）
* 情感表达（情绪线与反思）

**议论文（Argumentative）**

* 论点完整性（中心论点是否明确）
* 论据支持（事实/案例/数据）
* 逻辑衔接（论点—论据—论证链闭环）

> 规则引擎用于低级错误（连接词过度、句长异常、标点混用），LLM 用于高阶结构判断。

---

## 🚀 路线图（MVP）

* [x] PRD & 评价维度确定
* [x] FastAPI `/evaluate` 接口（返回 JSON）
* [ ] 前端 Demo 页（Streamlit/HTML）
* [ ] 示例数据与评估脚本
* [ ] PPT/Notion 作品集

---

## 🙌 致谢与来源

本项目为基于开源的二次开发与改造，参考：

* pmarcelino/**camoes**（LLM 驱动的作文评价思路）

> 已根据中文/英文、记叙文/议论文的教学场景进行重新定义与实现，输出结构、规则库与 Prompt 均为本仓库的自定义版本。
