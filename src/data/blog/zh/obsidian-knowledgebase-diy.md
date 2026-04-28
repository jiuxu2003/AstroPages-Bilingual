在 AI 浪潮席卷的今天，相信大家对 Markdown 这种轻量级标记语言已经再熟悉不过了。那么问题来了：**你平时都在用什么 Markdown 编辑器？**

什么什么？你说你还在用 Notepad++ 甚至 Windows 自带的记事本？那都多少年的老古董了！

你说你用 VSCode + Markdown 扩展？嗯，那还算凑合。但 VSCode 终究是一个为 Coding 而生的 IDE。如果你的诉求是**保存某次和大模型的精彩对话**，或者是**引用一个月前看过的一篇核心文献**，甚至想要**构建一套属于自己的知识库**…… 难道就没有更优雅的解法吗？

有的，兄弟。
快来加入我们 **Obsidian** 大军吧！选择 [Obsidian](https://obsidian.md/)，你将彻底改变你的知识管理工作流，并拥有以下极其舒适的体验：

---

### 1. 现代、美观且高度可定制的 UI
![image.png](https://webp.030727.xyz/blog/20260428143403379.png)

在这个颜值即正义的时代，一个赏心悦目的写作环境能极大提升记录的欲望。

- **开箱即用的极简美学：** Obsidian 的默认主题干净克制，专注于内容本身
    
- **疯狂的自定义能力：** 不喜欢默认外观？没关系！在外观设置中，你可以一键下载社区提供的数百款精美主题（比如广受开发者喜爱的 _Things_、_Minimal_ 主题， ~~还有笔者最爱的*Atom*主题~~）。
    
- **CSS Snippets 支持：** 如果你是前端大佬，你甚至可以自己写 CSS 像素级调整界面的每一个角落。你的笔记不仅是知识库，更是一件艺术品。
    

---



### 2. 丰富的插件生态（附 Git 同步实战）

![image.png](https://webp.030727.xyz/blog/20260428150853912.png)
Obsidian 的第三方插件市场目前拥有近 **3000** 个插件，你遇到的几乎所有痛点，社区里都已经有了现成的解法。比如说笔者经常使用的Git插件和Template插件，下面简要介绍一下Git插件的使用

环境准备：

**任意已下载[Git](https://git-scm.com/)和[Obsidian](https://obsidian.md/)的设备，一个[Github](https://github.com)账号**


**Step 1: 创建远程与本地仓库**
1. 创建github仓库
![截屏2026-04-28 16.14.44.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2016.14.44.png)

 2. 创建Obsidian仓库

![截屏2026-04-28 16.24.01.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2016.24.01.png)

**Step 2: 终端 Git 初始化**
在你的 Obsidian 仓库目录下打开终端（Windows 用户会在安装[Git](https://git-scm.com/)的时候一并安装，在对应的目录下右键然后就可以看到，在对应的目录下右键选择 **Open Git Bash Here**），依次执行以下命令：


```bash
# 1. 忽略 Obsidian 的本地工作区状态文件（避免多设备配置冲突）
cat <<EOF > .gitignore
.obsidian/workspace.json
.obsidian/workspace-mobile.json
EOF

# 2. 初始化本地 Git 仓库
git init

# 3. 将项目里的所有文件添加到暂存区（注意 add 和 . 之间有个空格）
git add .

# 4. 提交代码并添加注释信息
git commit -m "chore: initial commit"

# 5. 将当前分支重命名为 main
git branch -M main

# 6. 关联远程仓库（把链接替换为你实际的 URL）
git remote add origin https://github.com/你的用户名/你的仓库名.git

# 7. 首次推送并关联分支
git push -u origin main
```

> **💡进阶提示：处理网络问题**
> 
> 如果你在 `push` 时遇到上传速度极慢或 `connection error`，请在终端执行以下代理命令（注意将 `7890` 替换为你自己的魔法端口；如果你不懂什么是“魔法”…… 前方的区域过于危险，请以后再来探索吧）：
> 
> Bash
> 
> ```
> export https_proxy=http://127.0.0.1:7890
> export http_proxy=http://127.0.0.1:7890
> export all_proxy=socks5://127.0.0.1:7890
> ```

**Step 3: Obsidian 端配置全自动同步**
底层通道打通后，接下来让插件帮我们自动化：
1. 点击 Obsidian 左下角**小齿轮**打开设置。
    ![截屏2026-04-28 17.42.02.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2017.42.02.png)
2. 左侧选择**第三方插件 (Community plugins)** -> 关闭“安全模式” -> 点击**浏览**。
    ![image.png](https://webp.030727.xyz/blog/20260428174718611.png)
3. 搜索 **Obsidian Git** 并安装、启用。
    ![截屏2026-04-28 17.48.54.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2017.48.54.png)
    ![截屏2026-04-28 17.50.31.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2017.50.31.png)
4. 进入插件选项页，推荐如下设置：
	![截屏2026-04-28 17.52.59.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2017.52.59.png)
	- **Auto commit-and-sync interval (minutes):** 设为 `1`。
		
	- **Auto commit-and-sync after stopping file edits**:开启 ✅与上面选项搭配实现停止编辑一分钟后自动 commit，~~妈妈再也不用担心我丢进度了~~
        ![截屏2026-04-28 17.54.08.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2017.54.08.png)
    - **Pull updates on startup:** 开启 ✅（启动软件时自动拉取最新 commit，多设备无缝衔接）。
	    ![截屏2026-04-28 17.54.21.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2017.54.21.png)

> **🎁 其他宝藏插件推荐：**
> 
> [_Templater_](obsidian://show-plugin?id=templater-obsidian) (神级模板化工具), [_Excalidraw_](obsidian://show-plugin?id=obsidian-excalidraw-plugin) (内嵌无限画板), [_Outliner_](obsidian://show-plugin?id=obsidian-outliner) (大纲笔记利器), [_Better Export PDF_](obsidian://show-plugin?id=better-export-pdf), [_Image auto upload_ ](obsidian://show-plugin?id=obsidian-image-auto-upload-plugin)(图床自动上传)。
> 
> 仅作抛砖引玉，如果你有更硬核的需求，完全可以参考 [官方 API 文档](https://docs.obsidian.md/Home) 自己手搓一个

---

### 3.关系图谱
传统的文件夹管理是树状的，但人类的思维是网状的。

在 Obsidian 中，如果你在 **笔记 A** 里通过双括号 `[[笔记 B]]` 引用了 **笔记 B**
![image.png](https://webp.030727.xyz/blog/20260428201240869.png)
你就会在关系图谱中得到这样一条连线：
![image.png](https://webp.030727.xyz/blog/20260428201200641.png)
如果你坚持记录并建立链接，几个月后，你就会得到一个专属于你的、无比震撼的**知识星系**：

![image.png](https://webp.030727.xyz/blog/20260428200832306.png)

**Wow，是不是觉得 Amazing？**

随着你知识库规模的扩大，双向链接和图谱的作用才会真正浮现——它能帮你发现看似毫不相干的两个概念之间隐藏的联系，这就是“第二大脑”的魅力。

---

### 4. 拥抱未来：AI + 知识库
来到 Obsidian 1.12 版本，官方迅速地跟进了 CLI (命令行大模型 Agent) 的浪潮。其作者 kepano 甚至在 GitHub 上同步开源了专门服务于 Obsidian 仓库的 [Skills](https://github.com/kepano/obsidian-skills)。

可以通过往期文章 [告别环境混乱！使用 cc-switch 优雅管理多 AI Agent 的 MCP、Skills 与 API](https://blog.030727.xyz/posts/cc-switch-ai-agent-mcp-skills-api/) 学习CC-Switch的使用，然后在仓库管理添加*https://github.com/kepano/obsidian-skills* 后就能查询到对应的五个技能
![截屏2026-04-28 20.30.31.png](https://webp.030727.xyz/blog/%E6%88%AA%E5%B1%8F2026-04-28%2020.30.31.png)

![image.png](https://webp.030727.xyz/blog/20260428203154689.png)


这些技能能够直接读取你的Obsidian仓库，完美地将Ai总结、检索、生成的能力融入你的知识库工作流。


---

## *Ending*
在这个技术爆炸的时代，新工具和新名词层出不穷。我相信每个人的心里或多或少都会有些焦虑：“我到底用不用得上这东西？”

笔者的一点心得是：**对于新概念，先做粗浅的了解即可**（~~当然我也希望自己这种人的存在可以让大家了解的更快~~）。快速判断这个工具能否将你当前工作流中的某一个环节**转化为大模型（Token）可以处理的范畴**。

如果可以，**那就去实践，去燃烧你的 Token。**

如果没有实际需求就盲目跟风，只会陷入“差生文具多”的空虚感中——折腾了好几个小时配置，最后发现自己根本用不上。

找准痛点，用对工具，保持专注。

*(Life Learning & Happy coding!)*
