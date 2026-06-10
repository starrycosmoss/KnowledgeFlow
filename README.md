# 🚀 KnowledgeFlow

**AI-powered Personalized Knowledge Base & Intelligent Learning Recommendation Platform**

> 一个集成智能知识库、AI学习助手、项目推荐的一体化学习平台

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue)](https://www.python.org)
[![React 18+](https://img.shields.io/badge/react-18+-61dafb)](https://reactjs.org)
[![GitHub Stars](https://img.shields.io/github/stars/starrycosmoss/KnowledgeFlow?style=social)](https://github.com/starrycosmoss/KnowledgeFlow)

## ✨ 核心特性

### 🎯 智能学习路径
- 🤖 AI根据用户技能自动生成个性化学习计划
- 📊 实时技能评估和进度追踪
- 🎮 游戏化学习体验（等级、成就、排行榜）

### 📚 知识库系统
- 🌐 精选技术资源集合（教程、文档、项目）
- 🔗 知识图谱可视化展示技术关联关系
- 🔍 智能搜索和分类浏览

### 🤖 AI助手
- 💬 实时技术问答（基于RAG）
- 👨‍💻 代码审查和优化建议
- 🧠 概念解释和学习指导

### 🎁 项目推荐引擎
- ⭐ 基于技能匹配的开源项目推荐
- 📈 难度等级和预计学习时间评估
- 🏆 社区评分和趋势项目发现

### 👥 社区互动
- 💭 学习笔记分享
- 💬 讨论和评论
- 🤝 学习者互助和协作

---

## 🏗️ 项目架构

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend (React)                     │
│  Dashboard | Knowledge Base | AI Assistant | Projects   │
└──────────────────────┬──────────────────────────────────┘
                       │ REST API + WebSocket
┌──────────────────────▼──────────────────────────────────┐
│                 Backend (FastAPI)                       │
│  ├─ Auth Service      ├─ Recommendation Engine         │
│  ├─ User Management   ├─ AI Assistant Service          │
│  ├─ Knowledge DB      ├─ Knowledge Graph               │
│  └─ Learning Paths    └─ Skill Analyzer                │
└──────────────────────┬──────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┬──────────────┐
        │              │              │              │
    ┌───▼───┐    ┌────▼────┐   ┌────▼────┐   ┌────▼────┐
    │   PG  │    │ MongoDB │   │   Redis  │   │    ES   │
    │Database│   │  NoSQL  │   │ Cache    │   │ Search  │
    └────────┘    └─────────┘   └──────────┘   └─────────┘
```

---

## 🚀 快速开始

### 📋 前置要求

- **Python** 3.9+
- **Node.js** 18+
- **Docker** & **Docker Compose**
- **Git**

### 🔧 本地开发环境

#### 1️⃣ 克隆仓库

```bash
git clone https://github.com/starrycosmoss/KnowledgeFlow.git
cd KnowledgeFlow
```

#### 2️⃣ 使用 Docker Compose 启动（推荐）

```bash
# 启动所有服务（后端、前端、数据库、缓存等）
docker-compose up -d

# 查看日志
docker-compose logs -f

# 停止服务
docker-compose down
```

**服务地址**：
- 🌐 前端: http://localhost:3000
- 🔌 后端: http://localhost:8000
- 📚 API文档: http://localhost:8000/docs

#### 3️⃣ 手动启动（开发模式）

**后端**：
```bash
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

pip install -r requirements.txt
python app/main.py
```

**前端**：
```bash
cd frontend
npm install
npm run dev
```

---

## 📖 使用指南

### 1️⃣ 用户注册和技能评估

```bash
POST /api/auth/register
{
  "email": "user@example.com",
  "password": "secure_password",
  "username": "learner001"
}

# 技能评测
POST /api/users/skill-assessment
{
  "skills": ["Python", "JavaScript"],
  "experience_level": "intermediate"
}
```

### 2️⃣ 获取个性化学习路径

```bash
POST /api/recommendations/learning-path
{
  "goal": "Become a Full-Stack Developer",
  "current_skills": ["HTML", "CSS"],
  "available_hours_per_week": 15
}

# 响应示例
{
  "path_id": "path_123",
  "steps": [
    {"step": 1, "topic": "JavaScript Fundamentals", "duration": "2 weeks"},
    {"step": 2, "topic": "React Basics", "duration": "3 weeks"},
    ...
  ],
  "total_duration": "6 months",
  "difficulty_progression": "beginner → intermediate → advanced"
}
```

### 3️⃣ 浏览知识库

```bash
GET /api/knowledge/categories
GET /api/knowledge/search?q=react&category=frontend
GET /api/knowledge/{id}  # 获取知识项目详情
```

### 4️⃣ 与AI助手交互

```bash
POST /api/ai-assistant/chat
{
  "message": "怎样学习React中的Hooks？",
  "session_id": "session_abc123"
}

# WebSocket 实时对话
ws://localhost:8000/ws/chat/{session_id}
```

### 5️⃣ 获取推荐项目

```bash
GET /api/recommendations/projects?difficulty=intermediate&tags=react,nodejs
GET /api/recommendations/trending
GET /api/recommendations/personalized
```

---

## 📚 API 文档

完整的API文档请访问：
- 📖 [Swagger UI](http://localhost:8000/docs)
- 📋 [完整API文档](./docs/API.md)

**主要端点**：
- `POST /api/auth/register` - 注册
- `POST /api/auth/login` - 登录
- `GET /api/users/profile` - 用户信息
- `GET /api/knowledge/` - 知识库
- `POST /api/recommendations/learning-path` - 学习路径
- `POST /api/ai-assistant/chat` - AI对话
- `GET /api/recommendations/projects` - 项目推荐

---

## 🗄️ 数据库设计

### 核心表结构

**users**
```
id, email, username, password_hash, skill_level, 
total_learning_hours, created_at, updated_at
```

**knowledge_items**
```
id, title, description, category, content, 
difficulty_level, estimated_hours, tags, created_at
```

**learning_paths**
```
id, user_id, goal, steps_json, start_date, 
completion_percentage, status, updated_at
```

**recommendations**
```
id, user_id, item_id, type, score, created_at
```

**chat_history**
```
id, user_id, session_id, user_message, 
assistant_response, created_at
```

详见 [DATABASE_SCHEMA.md](./docs/DATABASE_SCHEMA.md)

---

## 🛠️ 开发指南

### 项目结构
```
KnowledgeFlow/
├── backend/          # FastAPI 后端
├── frontend/         # React 前端
���── docs/             # 文档
└── scripts/          # 工具脚本
```

### 环境变量配置

**.env.backend**
```
DATABASE_URL=postgresql://user:password@localhost/knowledgeflow
MONGODB_URL=mongodb://localhost:27017/knowledgeflow
REDIS_URL=redis://localhost:6379
OPENAI_API_KEY=your_openai_key
SECRET_KEY=your_secret_key
```

**.env.frontend**
```
VITE_API_URL=http://localhost:8000
VITE_WS_URL=ws://localhost:8000
```

### 开发工作流

```bash
# 1. 创建功能分支
git checkout -b feature/new-feature

# 2. 提交代码
git add .
git commit -m "feat: add new feature"

# 3. 推送并创建PR
git push origin feature/new-feature
```

详见 [DEVELOPMENT.md](./docs/DEVELOPMENT.md)

---

## 🧪 测试

```bash
# 后端测试
cd backend
pytest tests/

# 前端测试
cd frontend
npm run test

# 集成测试
npm run test:integration
```

---

## 📊 技术栈

### 后端
- **框架**: FastAPI
- **ORM**: SQLAlchemy
- **数据库**: PostgreSQL, MongoDB
- **缓存**: Redis
- **搜索**: Elasticsearch
- **AI**: LangChain, OpenAI API
- **任务队列**: Celery

### 前端
- **框架**: React 18
- **状态管理**: Redux / Zustand
- **样式**: Tailwind CSS
- **HTTP**: Axios
- **可视化**: D3.js, Three.js
- **构建**: Vite

### 基础设施
- **容器化**: Docker
- **编排**: Docker Compose / Kubernetes
- **CI/CD**: GitHub Actions

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

### 贡献步骤

1. Fork 本仓库
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交改动 (`git commit -m 'Add some AmazingFeature'`)
4. 推送分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

---

## 📝 许可证

本项目采用 **MIT License** - 详见 [LICENSE](LICENSE) 文件

---

## 🌟 致谢

感谢所有贡献者和支持者！

如果觉得项目有帮助，请给个 ⭐ Star！

---

## 📞 联系方式

- 📧 Email: contact@knowledgeflow.dev
- 🐦 Twitter: [@KnowledgeFlow](https://twitter.com/KnowledgeFlow)
- 💬 Discord: [Join Community](https://discord.gg/knowledgeflow)

---

**Made with ❤️ by starrycosmoss**