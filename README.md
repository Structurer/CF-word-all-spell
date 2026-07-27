# 单词背诵助手（拼写验证版）

这是一个基于浏览器的单词背诵与拼写练习项目，适合用来复习英语词汇、记忆词义和词组。项目包含两个静态页面入口文件和多组 JSON 词库数据。

## 目录结构

- `index.html` - 主页面入口，加载完整词库并支持拼写验证、词义隐藏/显示、单词顺序打乱等功能。
- `index preload.html` - 备选入口页面，包含预加载与实时进度展示方案。
- `styles.css` - 页面样式文件。
- `Vocabulary.json` - 根目录默认词库数据文件。
- `单词json/` - 分类词库文件夹：
  - `CET4_Vocabulary/Vocabulary.json`
  - `CET6_Vocabulary/Vocabulary.json`
  - `SAT_Vocabulary/Vocabulary.json`
  - `TOEFL_Vocabulary/Vocabulary.json`
  - `初中_Vocabulary/Vocabulary.json`
  - `考研_Vocabulary/Vocabulary.json`
  - `高中_Vocabulary/Vocabulary.json`

## 功能亮点

- 自动加载 JSON 词库并渲染单词卡片
- 拼写验证：输入单词后按回车验证正确性
- 双击回车可跳过当前单词
- 支持“隐藏/显示释义”操作
- 支持“随机打乱单词顺序”
- 右侧显示当前背诵进度
- 词卡支持滚动切换并自动定位当前单词

## 数据格式说明

词库采用 JSON 数组格式，每个单词对象示例：

```json
{
  "word": "absorb",
  "translations": [
    {
      "translation": "吸收（液体、气体等）",
      "type": "v"
    }
  ],
  "phrases": [
    {
      "phrase": "absorb in",
      "translation": "集中精力做某事；全神贯注于"
    }
  ]
}
```

字段说明：
- `word`：英语单词
- `translations`：释义列表，每项包含 `translation` 和词性 `type`
- `phrases`：可选项，常用搭配/短语及中文解释

## 使用方法

1. 将项目放在一个静态服务器上（例如 `http-server`, `Live Server` 等）。
2. 打开浏览器访问 `index.html` 或 `index preload.html`。
3. 页面加载完成后，可在右侧输入框输入单词并按回车。
4. 输入正确时会自动跳到下一个单词；双击回车可跳过当前单词。
5. 使用顶部按钮隐藏/显示释义，或打乱单词顺序。

> 注意：由于页面通过 `fetch` 加载本地 JSON 文件，建议使用 HTTP 服务而不是直接用 `file://` 打开页面。

## 运行示例

如果安装了 Node.js，可以使用简单服务器：

```bash
npx http-server .
```

然后访问 `http://127.0.0.1:8080/index.html`。

## 自定义词库

- 根目录的 `Vocabulary.json` 是默认加载的数据源。
- 如需切换其他词库，可替换根目录 `Vocabulary.json` 或修改页面脚本中的 `fetch` 路径。
- 每个分类词库文件均遵循相同 JSON 格式。

## 页面区别

- `index.html`：当前主版本，包含完整的词库渲染、拼写检查、打乱顺序、滚动定位等功能。
- `index preload.html`：备用版本，结构基本一致，但命名表明用于预加载/性能调优场景。

## 适用场景

- 英语单词拼写练习
- 词汇背诵与记忆强化
- 词义与常用短语复习

## 备注

当前项目为纯前端静态应用，不依赖构建工具。若希望扩展功能，可继续添加：

- 单词分类选择界面
- 正确率统计与错词复习
- 词汇搜索与筛选
- 更多本地词库切换功能
