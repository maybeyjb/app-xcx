# app-xcx
app和小程序
个人学习笔记：
笔记中的环境都为靶场环境。

# 新闻日报生成与分享系统

> viaiam - 这个项目由viaiam创建

## 🌟 功能特点

- 📰 **多源新闻聚合**：支持12个主流中文新闻源的内容抓取
- 🔍 **智能分类**：根据关键词自动分类为科技、金融、体育、娱乐和其他五大类
- ⏰ **24小时内新闻筛选**：只获取最近48小时内的热点新闻
- 📋 **Markdown日报生成**：将精选新闻整理成格式优美的日报
- 📊 **HTML可视化展示**：同时生成易于阅读的HTML版本
- ☁️ **词云分析**：自动生成新闻标题词云，一目了然把握热点
- 📧 **邮件定时发送**：支持设置定时任务，每天自动发送新闻摘要
- ⚙️ **跨平台兼容**：同时支持Windows、Linux和macOS系统

## 📡 支持的新闻源

1. 新浪科技
2. 腾讯科技
3. 网易科技
4. 搜狐科技
5. 凤凰科技
6. 新浪财经
7. 腾讯财经
8. 网易财经
9. 搜狐财经
10. 凤凰财经
11. 新浪体育
12. 新浪娱乐

## 📁 关键词分类

- **科技**：AI, 人工智能, 机器学习, 大数据, 区块链, 元宇宙, 云计算, 5G, 芯片, 自动驾驶, 机器人, 算法
- **金融**：股市, 基金, 投资, 理财, 银行, 保险, 经济, 汇率, 债券, 通胀, 央行, 监管
- **体育**：足球, 篮球, 奥运会, 世界杯, 比赛, 冠军, 运动员, 联赛, 训练, 赛事
- **娱乐**：电影, 电视剧, 明星, 演唱会, 综艺, 音乐, 奖项, 导演, 演员, 剧本
- **其他**：未被上述类别包含的新闻

## 🚀 安装依赖

```bash
pip install -r requirements.txt
```

依赖包包括：requests, beautifulsoup4, datetime, jieba, wordcloud, numpy, matplotlib, Pillow

## 💻 使用方法

### 基本使用

1. 安装依赖包
2. 运行新闻抓取脚本

```bash
python news_scraper.py
```

程序会自动抓取新闻，生成Markdown和HTML格式的日报，并存放在`output`目录下。

### 词云生成

新闻抓取完成后，运行词云生成脚本：

```bash
python generate_wordcloud.py
```

程序会从生成的新闻日报中提取标题，生成词云图片并保存到`output/wordcloud.png`。

### 定时任务和邮件发送

1. 首先编辑邮件配置文件：

```bash
# 复制并编辑邮件配置文件
cp email_config.json.example email_config.json
# 编辑配置文件，填入您的邮件信息
```

2. 添加定时任务（Windows需要管理员权限）：

```bash
python news_daily_task.py add-task
```

3. 手动运行任务发送邮件：

```bash
python news_daily_task.py run
```

## 🛠️ 自定义配置

### 新闻源配置

在`news_scraper.py`中，您可以修改`NEWS_SOURCES`列表来自定义要抓取的新闻源。

### 关键词配置

在`news_scraper.py`中，您可以修改`KEYWORDS`字典来自定义分类关键词。

### 词云配置

在`generate_wordcloud.py`中，您可以调整词云的大小、颜色、字体等参数。

### 邮件配置

在`email_config.json`中，您需要设置以下参数：

```json
{
  "sender": "your_email@example.com",
  "receiver": "recipient@example.com",
  "smtp_server": "smtp.example.com",
  "smtp_port": 587,
  "auth_code": "your_password_or_auth_code",
  "use_tls": true
}
```

### 定时任务配置

在`news_daily_task.py`中，您可以修改定时任务的执行时间和频率。

## 📋 注意事项

1. **Windows用户**：添加定时任务时需要以管理员身份运行命令提示符
2. **邮件配置**：请确保您的邮箱已开启SMTP服务，并使用正确的授权码
3. **日志文件**：程序运行日志保存在`news_daily.log`文件中
4. **API密钥**：如需使用DeepSeek API生成词云，请在`generate_wordcloud.py`中设置您的API密钥
5. **依赖安装**：如遇到中文字体问题，请确保您的系统中安装了中文字体

## 🤝 贡献指南

欢迎提交Issue和Pull Request来帮助改进这个项目！

## 📄 许可证

MIT License
