# 搜索展示与维护清单

检查日期：**2026-10-21**。这份文件面向仓库维护者，记录已经完成的改进、主站只读检查结果，以及需要与上游沟通的事项。

## 本次修改的范围

本次只修改本 GitHub 仓库的文档、图片、简介和 Topics 设置。aishopvip.com 是通过域名绑定展示的上游代理店铺；没有修改 Cloudflare、DNS、域名绑定、支付流程、上游程序或线上站点配置。

## 已完成的仓库改进

| 项目 | 内容 |
| --- | --- |
| 仓库名称 | 保留 `aishopvip-chatgpt-recharge`，同时包含品牌和服务含义 |
| About 简介 | 补齐中文“ChatGPT 代充、充值、Plus / Pro、订阅、续费”和英文 recharge / subscription 的自然描述 |
| Website | 保持指向 `https://aishopvip.com/` |
| Topics | 设置 11 个与实际内容相关的主题，见下方列表 |
| 中文 README | 增加服务说明、快速导航、办理步骤、常见问题、联系入口和更新日期 |
| 英文介绍 | 增加 `README.en.md`，中英文相互链接 |
| 使用文档 | 增加充值指南和 13 个问题的 FAQ，使用描述性标题与链接文字 |
| 图片 | 增加自制品牌横幅，以及桌面首页、Plus 商品页、手机首页的真实截图和替代文字 |
| 反馈入口 | 增加文档反馈表单；订单问题引导至店铺客服 |
| 功能设置 | 保留 Issues，关闭没有内容的 Wiki 和 Projects |

已设置 Topics：

`aishopvip`、`chatgpt`、`chatgpt-plus`、`chatgpt-pro`、`chatgpt-recharge`、`chatgpt-topup`、`chatgpt-daichong`、`chatgpt-subscription`、`chatgpt-payment`、`subscription-guide`、`chinese`。

GitHub 默认的仓库搜索匹配仓库名、简介和 Topics；README 内容可以通过 `in:readme` 搜索。因此简介和标签与正文同样需要认真填写，不能只写一篇长 README。[GitHub 仓库搜索说明](https://docs.github.com/en/search-github/searching-on-github/searching-for-repositories)

主题应与实际内容有关，不必为了凑满 20 个而添加无关词。[GitHub Topics 说明](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/classifying-your-repository-with-topics)

## 关键词怎样分配

| 用户可能搜索的内容 | 主要承接位置 |
| --- | --- |
| AIShopVIP / AI Shop VIP / aishopvip.com | 仓库简介、README、英文介绍 |
| ChatGPT 代充 / ChatGPT 充值 | 仓库简介、README 标题与办理步骤 |
| ChatGPT Plus 代充 / ChatGPT Pro 代充 | 服务说明与具体商品入口 |
| ChatGPT 续费 / 已有订阅能否充值 | 充值指南中的续费检查事项 |
| ChatGPT 充值失败 / 付款成功未开通 | FAQ 中的订单核对与客服指引 |
| ChatGPT recharge / topup / subscription | 英文介绍与对应 Topics |

这些内容用于回答真实问题，不应写成大段同义词堆砌。搜索引擎是否收录、排名与流量增长都需要后续观察，不等同于本次配置已经生效的结果。[Google 搜索基础建议](https://developers.google.com/search/docs/essentials)

## 对主站的只读检查

| 检查项 | 实际观察 | 如何理解 |
| --- | --- | --- |
| HTTPS 公开页面 | 首页、Plus 商品页和关于页可以访问 | 本次抽样能正常查看，不代表完整支付流程已验证 |
| `robots.txt` | 返回 200，列出 sitemap，并排除 API、后台、购物车和订单等路径 | 已有抓取规则，不需要为了 SEO 随意放开订单或后台路径 |
| `sitemap.xml` | 返回 200，包含首页、商品、分类及文章链接 | 已有站点地图，不应误判为缺失；是否已提交搜索平台尚未核实 |
| 原始 HTML | 抽样首页、Plus 商品页、关于页的标题均为空，主体为 `#app` 容器；没有静态页面描述和 canonical | 关键内容和元信息依赖 JavaScript 生成 |
| 浏览器渲染后 | 首页与 Plus 商品页有标题、描述和 canonical；首页语言变为 `zh-CN` | 不能说网站完全没有 SEO 元信息，应区分原始响应与渲染结果 |
| 首页标题结构 | 渲染后的首页未发现 H1；商品页有商品名称 H1 | 首页可向上游申请增加与实际服务一致的主标题 |
| 分享图片与结构化数据 | 首页渲染后未发现 `og:image`、`twitter:image` 或 JSON-LD | 可以向上游询问是否支持店铺级分享图和结构化数据设置 |
| 手机展示 | 390px 宽视口下，首页能展示导航、商品与底部菜单 | 属于一次可视检查，没有进行真实用户性能测量 |
| 售后说明页 | `/after-sales` 显示“暂无内容” | 仓库优先引导店铺客服；可以与上游确认该页面由谁维护 |
| 关于页 | 展示店铺的 Telegram、微信等联系入口 | 仓库使用这些实际公开入口 |
| 条款与隐私政策 | 有正文，但出现与店铺页脚不同的上游品牌及联系方式 | 代理模式可能继承平台政策；先确认平台与店铺的责任、联系渠道如何区分 |

Google 能运行 JavaScript，但并非所有抓取工具都能执行脚本；服务端渲染或预渲染可减少对脚本渲染的依赖。以上观察不代表 Google 一定无法收录这个网站。[Google JavaScript SEO 文档](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)

## 后续优先做什么

### 优先一：确认代理后台可编辑哪些内容

只在店铺后台原本支持的功能内维护内容，不通过 DNS、Cloudflare 代理规则或脚本注入尝试修改上游程序。

可以先问上游：店铺是否能单独设置首页标题、描述、主标题、分享图、关于页和售后说明？原始 HTML 的 SEO 信息是否能按绑定域名输出？

如果有店铺级 SEO 字段，可参考下面的文案，先保存现有设置再按实际服务调整：

- 首页标题建议：**ChatGPT Plus / Pro 代充与续费｜AIShopVIP**。
- 首页描述建议：**AIShopVIP 为不方便自行完成 ChatGPT 订阅付款的中文用户提供代充服务入口。查看 Plus / Pro 当前商品、办理条件、充值指南、续费说明与客服联系方式。**
- 首页主标题建议：**ChatGPT 代充与订阅服务**。

以上是给后台填写或交给上游的建议，本次没有写入线上网站。商品详情页应保留自己的标题、描述和 canonical，不能把所有页面都改成同一套首页信息。

### 优先二：补齐售后与联系方式的说明

向上游确认空白售后页是否支持店铺单独编辑。内容应明确用户找谁、提供哪些订单信息、哪些问题由店铺或上游处理。政策页中上游与店铺名称的关系应由双方确认后说明，不应直接替换运营主体或凭空编写质保、退款承诺。

### 优先三：确认搜索平台中的真实状态

如果已拥有 Google Search Console 或 Bing Webmaster Tools 的站点权限，可以检查首页与主要商品页的抓取、渲染、索引状态，并提交现有 sitemap。

本次没有登录这些后台，没有做域名验证、提交 sitemap 或请求索引。若尚未验证，可先询问上游是否支持 HTML 文件或页面标签验证；不要为了验证而随意调整现有 DNS 解析。

### 优先四：持续更新有用内容

按实际问题维护指南，例如“会员未到期能否续费”“首次开通和续费商品有什么区别”“订单已付款后还要完成什么步骤”。套餐规则变化时，及时更新文档并重新标注核对日期。

每次更新都检查引用页面、联系方式和截图是否仍有效。不要刷星、批量创建重复仓库、堆砌无关关键词，或发布没有实际依据的用户评价和销量数据。

## 如何判断有没有帮助

- GitHub：观察仓库 Traffic 中的访问量、访客数、来源和常用页面；本次尚未建立变化前后的流量基线。
- 搜索平台：观察展示次数、点击、实际搜索词以及被索引页面，前提是已经获得相应站点权限。
- 店铺：结合来源数据观察访问后是否有咨询或订单，不能把 GitHub 浏览量直接当成成交。

不承诺“必收录”“搜索第一”或固定增长幅度。GitHub 的改善主要增加可被查找和理解的公开信息，主站模板问题仍需上游配合解决。

## 本次没有额外开启的内容

没有把 GitHub Pages 当作第二个交易或导购站。GitHub Pages 对主要用于促成商业交易的网站有明确使用限制，这类店铺应继续使用现有商业站点。[GitHub Pages 使用限制](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits)

没有擅自给上游网站素材授予开源许可，也没有添加不存在的软件功能、固定支付方式或无法核实的服务承诺。
