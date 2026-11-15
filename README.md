# 民国公文速查

一个单页、离线可用的**民国公文速查工具**：文种、公文用语十二类、上行/平行/下行惯用辞令、通用例文、五版《公文程式》原文，另带「公文识读」——粘贴一篇公文，自动标出套语并生成识读报告。

- 纯静态单文件：`index.html`（HTML + CSS + JS + 数据全在里面）
- 无后端、无依赖、无外链资源，双击即可打开
- 手机 / 平板 / 桌面自适应，支持打印
- 内容 87 条套语、12 文种、12 类用语、四篇综合例文 + 十二文种示例、五版法规原文

---

## 目录结构

```
gongwen-online/
├── index.html    # 全部内容（单文件）
├── README.md     # 本文件
└── .nojekyll     # 供 GitHub Pages 跳过 Jekyll
```

---

## 本地打开

双击 `index.html` 用浏览器打开即可。

需要本地服务器时：

```bash
cd gongwen-online
python3 -m http.server 8000
# 访问 http://localhost:8000
```

---

## 部署到 GitHub Pages（推荐）

1. 新建仓库（Public），仓库名如 `gongwen`；
2. 把 `index.html`、`.nojekyll` 上传到**仓库根目录**（不要多套一层文件夹）；
3. `Settings → Pages → Source` 选 **Deploy from a branch**；
4. Branch 选 `main`，目录选 `/ (root)`，Save；
5. 等 1–2 分钟，访问：

```
https://<你的用户名>.github.io/gongwen/
```

> 想要更短网址 `https://<用户名>.github.io/`：仓库名直接命名为 `<用户名>.github.io`，其余步骤相同。

### 命令行方式

```bash
git init
git add index.html .nojekyll README.md
git commit -m "民国公文速查"
git branch -M main
git remote add origin https://github.com/<用户名>/gongwen.git
git push -u origin main
```

---

## 其他部署方式

- **Gitee Pages**：新建仓库 → 服务 → Gitee Pages → 部署分支 `main` → 启动（需实名）。
- **Netlify**：打开 <https://app.netlify.com/drop>，把整个 `gongwen-online` 文件夹拖进去，即刻得到网址。
- **Vercel**：导入仓库，Framework 选 Other，Build 留空，Output 留空，Deploy。
- **自有服务器 / 对象存储**：把 `index.html` 放进静态目录即可。

---

## 功能介绍

### 公文识读（本地运行）
粘贴公文 → 点「识读」→ 套语自动标红，点红字看释义；下方生成报告（命中数、行文方向统计、文种推测、高频套语）。
全部在浏览器本地完成，**不上传、不耗流量、零 API 成本**。

### 检索
顶栏搜索框按**词条名 / 拼音**匹配（如 `dengyin`、`dy`），结果展示该词条的释义、用在哪、例句、出处、辨析。

### 分类浏览
- 识读方法（四步法）
- 公文类别（12 文种，文种名与方向分行居中）
- 公文用语（12 类，小类导航）
- 上行 · 平行 · 下行惯用辞令（按方向，再按类别折叠）
- 通用例文（四篇综合 + 十二文种示例）
- 《公文程式》历次规则原文（1912—1928 五版，默认折叠）

---

## 自定义

- **加套语**：在 `index.html` 中找到 `const ITEMS = [`，按现有字段追加一条：
  `{t:"套语",p:"pinyin",ab:"首字母",d:"释义",u:"用在哪",e:"例句",s:"出处",n:"辨析",f:"用语类别",dir:"上行/平行/下行/通用",py:"带声调拼音"}`
- **改配色**：在 `:root` 中调整 CSS 变量（`--accent` 藏青、`--seal` 印章朱、`--bg` 纸色等）。
- **换例文**：搜索 `tpl-lifa`（综合例文）与 `tpl-li12`（十二文种示例）。

---

## 说明与免责

- 分类框架与用语体系参照汪海涛《如何识读民国公文档案？》。
- 法规原文据《临时政府公报》《政府公报》及维基文库校录，条文以原件用字为准。
- **例文均为虚构示例，非真实档案**，仅供演示与学习，不可作为史料引用。
- 本工具为学习辅助，具体文书中的含义仍需结合上下文判断。

## 许可

内容采用 **CC BY-NC-SA 4.0**（署名—非商业性使用—相同方式共享）；代码部分可视为 **MIT**。
