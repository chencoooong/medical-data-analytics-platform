# 医疗大数据分析和预测平台

一个完整的医疗数据分析、预测和决策支持系统，用于早期疾病预警、优化诊疗方案、降低患者再入院率。

## 🏥 核心功能

- **数据摄入** - 支持多源医疗数据接入（病历、检验、影像、生命体征等）
- **数据处理** - ETL、数据清洗、特征工程
- **疾病预警** - 基于机器学习的早期疾病预警
- **再入院率预测** - 预测患者再入院风险
- **诊疗优化** - 数据驱动的治疗方案推荐
- **可视化仪表板** - 实时数据监控和分析
- **决策支持** - 医生辅助诊疗工具

## 📊 系统架构

```
┌─────────────────────────────────────────────────────────────────┐
│                     前端应用层                                  │
│           (React Dashboard + ECharts Visualization)             │
└─────────────────────────────────────────────────────────────────┘
                              ↑
┌─────────────────────────────────────────────────────────────────┐
│                    API 服务层 (FastAPI)                          │
│  (数据查询、预测接口、决策支持、实时监控)                        │
└─────────────────────────────────────────────────────────────────┘
         ↑                    ↑                    ↑
┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
│   分析引擎       │  │   预测模型       │  │   特征工程       │
│  (统计分析)      │  │  (ML/DL)         │  │  (数据处理)      │
└──────────────────┘  └──────────────────┘  └──────────────────┘
         ↓                    ↓                    ↓
┌─────────────────────────────────────────────────────────────────┐
│                 数据存储层                                       │
│  (PostgreSQL + ClickHouse + MongoDB + Redis)                    │
└─────────────────────────────────────────────────────────────────┘
         ↑                    ↑                    ↑
┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
│  HIS 系统        │  │  检验系统        │  │  影像系统        │
└──────────────────┘  └──────────────────┘  └──────────────────┘
```

## 🚀 快速开始

### 环境要求
- Python 3.9+
- PostgreSQL 13+
- Docker & Docker Compose

### 安装

```bash
# 克隆仓库
git clone https://github.com/chencoooong/medical-data-analytics-platform.git
cd medical-data-analytics-platform

# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Linux/Mac
# 或
venv\Scripts\activate  # Windows

# 安装依赖
pip install -r requirements.txt
```

### 启动服务

```bash
# 使用 Docker Compose
docker-compose up -d

# 或手动启动
python -m uvicorn app.main:app --reload --port 8000
```

访问 API 文档：http://localhost:8000/docs

## 📁 项目结构

```
medical-data-analytics-platform/
├── app/                           # 主应用程序
│   ├── main.py                   # FastAPI 应用入口
│   ├── config.py                 # 配置管理
│   ├── database.py               # 数据库连接
│   ├── models/                   # 数据模型
│   │   ├── patient.py           # 患者模型
│   │   ├── medical_record.py    # 病历模型
│   │   └── prediction.py        # 预测结果模型
│   ├── api/                      # API 路由
│   │   ├── patients.py          # 患者接口
│   │   ├── records.py           # 病历接口
│   │   ├── predictions.py       # 预测接口
│   │   └── analytics.py         # 分析接口
│   ├── services/                 # 业务逻辑
│   │   ├── data_processor.py    # 数据处理
│   │   ├── feature_engineer.py  # 特征工程
│   │   ├── prediction_engine.py # 预测引擎
│   │   └── analysis_engine.py   # 分析引擎
│   ├── ml/                       # 机器学习模块
│   │   ├── models.py            # 模型定义
│   │   ├── trainer.py           # 模型训练
│   │   └── predictor.py         # 预测执行
│   └── utils/                    # 工具函数
│       ├── logger.py            # 日志
│       ├── validators.py        # 数据验证
│       └── decorators.py        # 装饰器
│
├── data/                          # 数据目录
│   ├── raw/                      # 原始数据
│   ├── processed/                # 处理后数据
│   └── models/                   # 训练好的模型
│
├── tests/                         # 测试文件
│   ├── test_api.py              # API 测试
│   ├── test_services.py         # 服务测试
│   └── test_ml.py               # ML 测试
│
├── notebooks/                     # Jupyter notebooks
│   ├── exploratory_analysis.ipynb
│   ├── model_training.ipynb
│   └── data_visualization.ipynb
│
├── docker-compose.yml             # Docker 编排
├── Dockerfile                     # Docker 镜像
├── requirements.txt               # Python 依赖
├── .env.example                   # 环境变量示例
└── README.md                      # 项目文档
```

## 🛠 技术栈

- **后端框架**: FastAPI
- **数据处理**: Pandas, NumPy, PySpark
- **机器学习**: Scikit-learn, XGBoost, TensorFlow
- **数据库**: PostgreSQL, ClickHouse, Redis
- **消息队列**: Apache Kafka
- **容器化**: Docker, Kubernetes
- **前端**: React, ECharts

## 📈 核心模块说明

### 1. 数据摄入层
- 支持 HL7/FHIR 标准医疗数据格式
- 实时数据流处理（Kafka）
- 批量数据导入（CSV、数据库）

### 2. 数据处理层
- 数据清洗和验证
- 缺失值处理
- 异常检测
- 数据脱敏和隐私保护

### 3. 特征工程
- 自动特征提取
- 特征选择和优化
- 时间序列特征
- 临床特征组合

### 4. 预测模型
- **早期疾病预警**: XGBoost, Random Forest
- **再入院率预测**: Gradient Boosting, Neural Network
- **诊疗优化**: 聚类分析, 关联规则挖掘

### 5. 决策支持
- 个性化治疗方案推荐
- 药物相互作用检查
- 最佳实践对标

## 📊 数据字典

### 患者表 (patients)
- patient_id: 患者ID
- name: 患者姓名
- age: 年龄
- gender: 性别
- admission_date: 入院日期
- discharge_date: 出院日期

### 病历表 (medical_records)
- record_id: 病历ID
- patient_id: 患者ID
- diagnosis: 诊断
- treatment: 治疗方案
- medications: 用药
- vital_signs: 生命体征

### 预测结果表 (predictions)
- prediction_id: 预测ID
- patient_id: 患者ID
- prediction_type: 预测类型
- risk_score: 风险评分
- confidence: 置信度

## 🔐 安全和隐私

- 患者数据脱敏处理
- 基于角色的访问控制 (RBAC)
- 数据加密存储和传输
- 审计日志记录
- HIPAA/GDPR 合规

## 📝 API 文档

详见 `docs/API.md`

## 🧪 测试

```bash
# 运行所有测试
pytest

# 运行特定测试
pytest tests/test_api.py -v

# 生成覆盖率报告
pytest --cov=app tests/
```

## 📚 文档

- [架构设计文档](docs/ARCHITECTURE.md)
- [API 文档](docs/API.md)
- [数据字典](docs/DATA_DICTIONARY.md)
- [部署指南](docs/DEPLOYMENT.md)

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 📄 许可证

MIT License

## 👥 团队

医疗大数据分析团队

## 📞 联系方式

- Email: team@hospital.com
- Documentation: https://docs.hospital.com
