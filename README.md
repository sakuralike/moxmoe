# moxmoe · 萌导航

moxmoe 是一个面向个人站长和小团队的萌系网址导航项目，目标是把分类浏览、站内搜索、浏览器收藏与站点内容维护整合在同一个可自托管应用中。界面采用草莓粉主色、圆角卡片、柔和背景光斑和明暗主题，覆盖访客前台与管理后台。

仓库：[sakuralike/moxmoe](https://github.com/sakuralike/moxmoe)

**当前仓库仍是静态 UI 原型，不是已经完成的导航系统。** 现有内容为 27 个 HTML 页面，其中前台 4 个、后台 23 个，以及 2 个公共 CSS 文件。页面中的网站、统计、任务状态和操作结果主要用于演示；尚未接入服务器、数据库或真实身份认证。

## 当前可以做什么

- 浏览首页、分类页、投稿页、404 页面，以及管理后台各模块的界面。
- 查看亮色、暗色和跟随系统主题；部分页面会在浏览器本地保存主题偏好。
- 演示收藏按钮状态、提示消息、链接新增弹窗、表格全选和部分审核交互。
- 查看公共设计变量与组件样式，包括卡片、搜索框、表单、表格、弹窗和后台布局。
- 在浏览器中直接预览，无需安装 Node.js、PHP、MySQL 或 Docker。

### 原型与真实业务的区别

| 功能 | 当前实际行为 | 尚未实现的部分 |
| --- | --- | --- |
| 首页与分类 | 使用写死的示例内容；分类页由内联脚本生成卡片 | 数据库查询、发布状态过滤、真实分页 |
| 站内搜索与搜索源 | 展示输入框、按钮和搜索源配置样式 | 查询结果、关键词处理、搜索源跳转逻辑 |
| 主题切换 | 可以切换明暗主题；部分页面读写 `moenav:theme` | 所有页面一致的偏好持久化与异常处理 |
| 收藏 | 点击后改变按钮状态 | 刷新恢复、跨页面同步、真实收藏列表 |
| 收藏导出 | 会下载 JSON，但其中 `favorites` 固定为空数组 | 导出实际收藏、导入与数据校验 |
| 后台登录 | 任意非空账户与密码都只会触发延迟跳页 | 账户验证、密码哈希、会话、访问控制与限流 |
| 游客投稿 | 浏览器校验部分字段后显示模拟成功结果 | 服务端校验、数据保存、防滥用与审核流程 |
| 链接保存与投稿审核 | 弹窗、提示或当前页面元素变化 | 真实增删改查、事务、权限检查与操作审计 |
| 统计、备份、巡检与服务状态 | 静态示例或表单界面 | 真实统计、可恢复备份、网络巡检与任务执行 |
| 导入导出与各类设置 | 后台页面原型 | 文件处理、设置保存及前台联动 |
| 关于、隐私与条款 | 页脚包含占位入口 | 完整法律说明页面及实际站点信息 |

后台 HTML 可以直接访问，登录页不构成安全屏障。请勿输入真实管理员密码、个人资料或生产凭据，也不要将这些页面作为具备管理能力的正式站点部署到公网。页面里的“已保存”“提交成功”“服务正常”等文案不代表对应业务已经完成。

## 页面索引

下列路径都是当前静态文件，不是未来 Laravel 应用的路由。

### 访客前台

| 文件 | 页面内容 |
| --- | --- |
| [index.html](index.html) | 首页、搜索区、收藏区、分类导航与示例链接 |
| [category.html](category.html) | 分类详情、链接宫格、筛选和分页样式 |
| [submit.html](submit.html) | 网站投稿表单、字段提示与模拟成功页 |
| [404.html](404.html) | 404 视觉原型与返回入口 |

直接打开 `404.html` 只是在预览错误页；它不会自动为其他不存在的路径配置 HTTP 404 响应。

### 管理后台

| 文件 | 页面内容 |
| --- | --- |
| [admin/login.html](admin/login.html) | 登录界面 |
| [admin/dashboard.html](admin/dashboard.html) | 仪表盘 |
| [admin/links.html](admin/links.html) | 链接管理 |
| [admin/categories.html](admin/categories.html) | 分类管理 |
| [admin/tags.html](admin/tags.html) | 标签管理 |
| [admin/submissions.html](admin/submissions.html) | 投稿审核 |
| [admin/announcements.html](admin/announcements.html) | 公告管理 |
| [admin/banners.html](admin/banners.html) | 轮播图管理 |
| [admin/analytics.html](admin/analytics.html) | 访问统计 |
| [admin/link-stats.html](admin/link-stats.html) | 链接数据 |
| [admin/deadlink.html](admin/deadlink.html) | 死链巡检 |
| [admin/import-export.html](admin/import-export.html) | 导入导出 |
| [admin/backup.html](admin/backup.html) | 备份还原 |
| [admin/logs.html](admin/logs.html) | 操作日志 |
| [admin/status.html](admin/status.html) | 服务状态 |
| [admin/site-info.html](admin/site-info.html) | 站点信息 |
| [admin/theme.html](admin/theme.html) | 主题配置 |
| [admin/wallpaper.html](admin/wallpaper.html) | 壁纸配置 |
| [admin/seo.html](admin/seo.html) | SEO 设置 |
| [admin/search-sources.html](admin/search-sources.html) | 搜索源配置 |
| [admin/switches.html](admin/switches.html) | 全局开关 |
| [admin/security.html](admin/security.html) | 安全设置 |
| [admin/admins.html](admin/admins.html) | 管理员与角色 |

界面覆盖范围不等于首发功能承诺。例如多管理员、任意壁纸上传、轮播广告与自定义搜索源管理，不会因为已有设计稿就自动进入第一阶段。

## 目录结构

`mox-moe+` 是项目主目录，也是 Git 仓库根目录。当前主要文件如下：

```text
mox-moe+/
  .gitignore
  README.md
  index.html
  category.html
  submit.html
  404.html
  css/
    tokens.css
    components.css
  admin/
    login.html
    dashboard.html
    ...                  其余管理页面见页面索引
```

- `css/tokens.css` 定义颜色、明暗主题、字号、间距、圆角、阴影、动效和基础布局变量。
- `css/components.css` 提供按钮、表单、链接卡片、提示、弹窗、表格及后台布局等公共样式。
- HTML 文件还包含各页的局部样式和内联 JavaScript，目前没有独立的前端应用构建流程。
- 字体名称是 CSS 候选字体栈，并不代表仓库已经包含或加载这些字体文件；实际呈现取决于本机可用字体。
- 样式中已有响应式断点、焦点样式和减弱动效处理，但这不等于已完成全部设备适配或可访问性验收；后台当前以桌面预览为主。

## 本地预览

### 方式一：直接用浏览器打开

用现代浏览器打开仓库根目录的 `index.html` 即可。后台可直接打开 `admin/dashboard.html`，也可以从 `admin/login.html` 体验模拟登录过程。

这种方式不需要安装依赖。不同浏览器对 `file://` 页面的本地存储行为可能不同，如需检查主题偏好或跨页行为，使用本地 HTTP 预览更合适。

### 方式二：使用 PHP 本地 HTTP 服务

在已安装 PHP 且 `php` 可在当前终端调用的情况下，于项目根目录执行：

```powershell
php -S 127.0.0.1:18080 -t .
```

执行命令前确认当前目录包含 `index.html`。`18080` 是示例端口；如被占用或处于 Windows 保留端口范围，请改用其他可用端口。

启动后访问：

- 首页：<http://127.0.0.1:18080/index.html>
- 分类：<http://127.0.0.1:18080/category.html>
- 投稿：<http://127.0.0.1:18080/submit.html>
- 后台：<http://127.0.0.1:18080/admin/dashboard.html>

在终端按 `Ctrl+C` 停止服务。该命令只把当前 HTML/CSS 作为静态资源提供，不会启动 Laravel、创建数据库或实现后台功能。只绑定 `127.0.0.1`，不要把 PHP 内置开发服务器用于正式部署。

当前仓库没有 `composer.json`、`package.json`、`artisan`、数据库迁移、自动化测试配置或 Docker 编排文件，因此不存在可直接执行的项目安装、构建、迁移或应用容器启动命令。预览页面不需要先创建这些文件。本机单独配置的开发数据库见下文，它不代表应用已经接入数据库。

## 后续开发所需环境

下表描述正式应用的开发基线，不表示这些依赖已被引入当前源码，也不表示正式应用已经可运行。

| 工具或服务 | 用途 | 需求 |
| --- | --- | --- |
| Git | 源码管理与远程仓库连接 | 使用本机已有安装 |
| PHP | 应用运行与命令行任务 | 8.4 当前安全补丁版 |
| Composer | 安装与锁定 PHP 依赖 | 2.x；正式开发时使用 |
| Node.js 与 npm | Vite 开发和资源构建 | 满足所选 Vite 版本的 `engines` 要求；引入构建工具时验证 |
| MySQL | 业务数据、迁移与集成测试 | 8.4 LTS 当前安全补丁版 |
| Docker / Compose | 隔离数据库与验证运行环境 | 可复用本机 Docker；静态预览不依赖它 |
| 浏览器 | 页面预览与交互检查 | 现代 Chromium、Firefox 或 Safari |

本机开发工具和后续补齐的环境安装在 `D:\kfhj`，项目源码仍位于 `E:\只比主题\moe网址导航\mox-moe+`。已有 Docker 可直接复用，无需为了静态预览再安装一套。Docker 客户端存在不等于引擎正在运行，也不等于已经有可连接的 MySQL 实例。

计划使用的 PHP 扩展包括 Ctype、cURL、DOM、Fileinfo、Filter、Hash、Mbstring、OpenSSL、PCRE、PDO、Session、Tokenizer、XML，以及 PDO MySQL、Intl、GD、Zip。实际安装检查需要同时核对扩展、可写目录、数据库连接及目标宿主限制，不能只检查 `php -v`。

### 当前 Windows 开发机

以下是 2026-10-13 本次初始化的实测结果，仅描述这台开发机，不要求其他克隆者使用相同磁盘路径。

| 工具或服务 | 已验证版本 | 本机位置或连接 |
| --- | --- | --- |
| Git | 2.55.0.windows.2 | `D:\kfhj\01-Git\Git` |
| Node.js / npm | 26.1.0 / 11.13.0 | `D:\kfhj\04-Node.js\26.1.0\node-v26.1.0-win-x64` |
| PHP CLI | 8.4.26 NTS x64 | `D:\kfhj\10-PHP\8.4.26` |
| Composer | 2.10.3 | `D:\kfhj\10-PHP\Composer\2.10.3` |
| Docker Engine / Compose | 29.8.1 / 5.5.1 | 复用 `D:\kfhj\12-Docker-WSL` 中的现有安装 |
| MySQL | 8.4.11 | Docker 容器 `moxmoe-mysql84`，`127.0.0.1:33084` |

PHP 和 Composer 安装包已与官方 SHA-256 校验值比对；PHP 所需扩展、Argon2id、Composer 网络与平台诊断已通过。PHP 8.3 原有目录保留，没有迁移或覆盖。新增 PHP/Composer 目录已加入用户 PATH；已打开的终端可能需要重新启动以读取更新后的环境。

Composer 的 home、cache 和临时目录均位于 `D:\kfhj\10-PHP\Composer`；PHP 临时、会话及日志目录位于 `D:\kfhj\13-包缓存\php`。已有 npm 缓存继续使用 `D:\kfhj\13-包缓存\npm`。

开发数据库配置保存在仓库外的 `D:\kfhj\24-Moxmoe\mysql84\compose.yaml`，使用固定镜像 digest、独立 named volume `moxmoe_mysql84_data` 和仅限本机的端口映射。Docker 的活动 ext4 数据盘已核对位于 `D:\kfhj\12-Docker-WSL\wsl-data\disk\docker_data.vhdx`，没有把 MySQL 活动数据目录直接绑定到 Windows NTFS。

```powershell
# 查看、启动或停止本项目的开发数据库，不影响其他项目容器。
docker compose -f D:\kfhj\24-Moxmoe\mysql84\compose.yaml ps
docker compose -f D:\kfhj\24-Moxmoe\mysql84\compose.yaml up -d
docker compose -f D:\kfhj\24-Moxmoe\mysql84\compose.yaml stop
```

数据库名为 `moxmoe_dev`，应用账号为 `moxmoe`。随机密码保存在该环境目录内受 Windows ACL 限制的 `secrets/app_password`，管理员密码另存 `secrets/root_password`；不在 README、Git 配置或源码中记录密码值。当前只创建空开发数据库，没有 Laravel 表。PHP PDO 已验证连接、中文/Emoji 往返和事务回滚，验证使用临时表，结束后业务表数量仍为零。

## 应用实施方向

以下内容是待实现方案，与前面的原型现状分开描述。

### 技术路线

采用 **PHP 8.4 + Laravel 13 + Blade + 原生 JavaScript + Vite + MySQL 8.4** 的单应用结构：

```text
浏览器
  -> Nginx / Apache + PHP-FPM
  -> Laravel
       -> Blade 服务端渲染前台与后台
       -> 表单校验、会话认证和业务操作
       -> MySQL 数据持久化
       -> 私有存储、任务执行与审计
```

选择这条路线是为了保留现有 HTML/CSS 的视觉资产，用 Blade 接入真实数据，而不是再引入独立 API 服务和后台 SPA。原生 JavaScript 负责主题、收藏、弹窗等局部交互；公开内容以服务端 HTML 输出，减少搜索引擎和基础浏览对脚本的依赖。

Laravel 应用后续以当前 `mox-moe+` 为项目根逐步建立，不另建平行项目作为主目录。现有页面会迁移为模板与公共布局，但本次 README 不代表框架骨架已经创建。

Vite 和 Node.js 用于开发与构建，不作为生产 Web 服务。预期发行包包含生产 PHP 依赖和已构建静态资源；这仍是交付目标，并非当前仓库已经提供的一键安装包。

### 核心功能边界

- 内容管理：两级分类、标签、链接编辑、发布与归档、精选和排序；前台按统一公开状态读取内容。
- 访客体验：服务端渲染首页、分类与搜索；浏览器本地收藏及真实导入导出；明暗与系统主题。
- 管理安全：首发单管理员，服务端会话、CSRF 防护、密码哈希、登录限流和关键操作审计。
- 数据保护：可校验的站点数据备份与恢复；恢复前保护性备份；中断与失败必须有可恢复状态。
- 公开运营：游客投稿经审核后收录；链接巡检只提供状态与人工处理依据，不自动删除网站。
- 运行维护：手动分批任务与可选定时调度共用实现；不要求首发运行 Redis 或常驻队列集群。

第一阶段不引入访客注册、跨设备收藏同步、多站点管理、细分管理员角色、推荐算法或广告系统。站外搜索先采用固定模板，搜索源管理界面不直接转为任意 URL 模板执行能力。

### 实施阶段与验收

| 阶段 | 实施内容 | 完成依据 |
| --- | --- | --- |
| 环境与技术验证 | PHP/MySQL、构建、文件隔离、搜索与备份验证 | 在目标环境中实际运行，不以“工具已安装”替代 |
| 应用基础 | Laravel、Blade 布局、安装、管理员、会话与基础设置 | 初始化、登录/登出、CSRF、失败重试可验证 |
| 内容闭环 | 分类、标签、链接、前台展示、搜索、收藏与点击聚合 | 后台真实新增后前台可见；收藏刷新不丢失 |
| 数据保护 | 分批任务、备份、恢复与维护模式 | 在隔离数据库恢复并核对内容；失败不误报成功 |
| 运营功能 | 投稿审核、内容导入导出、巡检与定时任务 | 用真实数据完成流程，权限与输入校验同时通过 |
| 发布验证 | 打包、目标主机安装、性能、安全与升级恢复 | 完整环境验收后才宣称可公开部署 |

开发测试计划包括 PHP 单元与功能测试、MySQL 8.4 集成测试以及浏览器端到端测试。5000 条链接是规划中的搜索验收数据规模，不是当前已经测出的性能成绩；页面数量也不是业务完成度。

## 部署与安全前提

正式应用的目标环境是具备 HTTPS 的 Linux VPS 或面板主机，使用 Nginx/Apache、PHP-FPM 8.4 与 MySQL 8.4。Windows 本地预览通过，不等于这些生产条件已经得到验证。

后续正式部署需要满足：

- Web 根目录只指向 Laravel 的 `public/`，源码、`.env`、日志、会话、临时上传与备份不能直接下载。
- 使用专用数据库及适当权限的专用账户，不把全局数据库管理员凭据写入应用。
- 所有后台写操作执行服务端认证、授权与输入校验；前端按钮隐藏不能代替访问控制。
- 投稿、导入和文件上传有明确大小与类型限制；链接巡检必须具备 SSRF 防护。
- 备份不仅要能下载，还要在隔离环境中完成恢复核对；升级不得以清库或重新填充演示数据代替迁移。

当前静态原型不具备上述应用层保护。共享主机是否满足 PHP、数据库、目录隔离和任务执行要求，需要逐台验证，不能默认兼容。

## 仓库范围与许可

Git 仓库边界为 `mox-moe+` 本身，不是其父目录。`项目规划文档/`、`.workbuddy/` 和 `.playwright-mcp/` 不属于推送内容；同名目录即使放入项目根，也应由忽略规则排除。环境安装目录、数据库数据、凭据和运行缓存不属于源码。

阅读本 README 和仓库中的页面即可了解当前内容，不需要取得父目录中的本地规划资料。远程仓库地址不表示本地修改已经提交或推送，实际状态以 Git 记录为准。

当前未附带 `LICENSE` 文件，不能据此认定代码或界面素材已按 MIT、Apache-2.0 等许可证授权。后续如采用第三方代码、字体或素材，需要分别核对其许可与署名要求。
