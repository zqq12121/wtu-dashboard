# 武汉纺织大学招生就业数据分析平台

> 数据库原理课程设计 | Python · MySQL · Chart.js

🔗 **在线预览：** [https://zqq12121.github.io/wtu-dashboard](https://zqq12121.github.io/wtu-dashboard)

---

## 项目简介

基于武汉纺织大学 2022–2024 年**真实公开数据**，构建招生就业一体化数据分析看板。涵盖数据采集、清洗标准化、MySQL 建库、可视化看板全链路，模拟企业级 BI 数据治理流程。

---

## 技术栈

| 层级 | 技术 |
|------|------|
| 数据清洗 | Python（pandas、numpy、re） |
| 数据存储 | MySQL · 星型模型（1 事实表 + 4 维度表） |
| 可视化 | Chart.js · 原生 HTML/CSS/JS |
| 部署 | GitHub Pages |

---

## 核心功能

- **招生分析** — 湖北省主要专业录取最低分趋势（2022–2024）、全国 21 省份横向对比、超省控线分差排行
- **就业分析** — 就业率趋势、毕业去向分布、就业地域热力、行业分布
- **数据治理看板** — 数据完整度、异常值占比、重复率监控，完整展示 ETL 处理链路
- **预警监控** — 关键指标三级状态预警（正常 / 关注 / 历史低位）
- **交互筛选** — 年份 Tab 切换（2022 / 2023 / 2024 / 全览对比）

---

## 数据来源

- 武汉纺织大学信息公开网 [xwgk.wtu.edu.cn](https://xwgk.wtu.edu.cn)
- 武汉纺织大学本科招生网 [zsb.wtu.edu.cn](https://zsb.wtu.edu.cn)
- 中国教育在线 / 大学生必备网（辅助核验）

---

## 数据库设计

采用**星型模型**，以招生事实为中心：

```
fact_enrollment（招生事实表）
  ├── dim_province（省份维度）
  ├── dim_major（专业维度）
  ├── dim_score_line（分数线维度）
  └── dim_employment（就业维度）
```

---

## 项目结构

```
wtu-dashboard/
├── index.html          # 可视化看板（单文件，含全部图表逻辑）
├── data_processing/
│   ├── 01_clean_data.py    # 数据清洗与标准化
│   ├── 02_load_db.py       # MySQL 批量入库
│   └── 03_query_examples.py # 常用查询示例
└── enrollment_db.sql   # 完整建库脚本（含视图、索引、约束）
```

---

## 快速运行

```bash
# 安装依赖
pip install pandas numpy sqlalchemy pymysql

# 数据清洗
python data_processing/01_clean_data.py

# 导入数据库（需本地 MySQL）
python data_processing/02_load_db.py

# 看板直接用浏览器打开
open index.html
```

---

## 部分数据指标

| 指标 | 数值 |
|------|------|
| 2023届就业率 | 91.99% |
| 2023届升学率 | 25.76% |
| 2024届留鄂比例 | 57.16% |
| 2024年湖北物理类省控线 | 437分 |
| 热门专业最高超线分差 | +128分（会计学） |
| 数据清洗完整度 | 96.4% |
