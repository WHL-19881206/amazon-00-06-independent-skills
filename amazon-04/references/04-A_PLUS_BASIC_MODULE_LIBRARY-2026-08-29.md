# Reference｜A+ Built-in Module Library

> 从 2026-08-29 原版 04 原样迁移。它是静态/候选模块知识库，不是每次执行都必须全部加载的 Runtime 指令。执行时先确定 Basic/Premium 与候选模块，再只读取相关模块定义；当前 Amazon UI/模块能力与本 Reference 冲突时，以当前官方/账户事实为准。

## 6A. BUILT-IN A+ MODULE LIBRARY｜基础 A+ + Premium A+ 全模块内置基线

> 本节是 04 的**内置模块知识库**，直接吸收用户提供的《基础A+》与《高级A+》PDF 中的全部模块定义；**不替代**上文 `DYNAMIC MODULE CATALOG` 与当前 Seller Central / Amazon Policy 核查机制。
>
> - Basic A+ 来源：`Basic A+ Module Guide｜基础 A+ 模块指南｜仅 PC 端`，Version 1.3，2026-08-29；模块顺序按 Seller Central “Add Module”，规格按官方 SP-API A+ Content Examples。
> - Premium A+ 来源：`Premium A+ Module Guide`，Version 1.0，Last updated 2023-05-30。
> - 运行原则：以下内容作为 `BUILT_IN_MODULE_BASELINE`。正式生产时仍必须读取当前目标账户/Marketplace 可用模块；如当前 UI、政策或字段约束与本内置基线冲突，以当前已验证平台事实为准，并记录 `MODULE_CATALOG_DEVIATION`，不得静默改写历史基线。
> - 用户长期生产标准仍保持：Basic/Premium 默认均规划 7 个总内容模块；本节的“模块库数量”不等于单次 A+ 必须使用的模块数量。

### 6A.1 EMBEDDED MODULE SCHEMA｜内置模块统一字段

每次做模块选择时，先从本节映射到统一结构：

```text
MODULE_TYPE_ID
MODULE_NAME
A_PLUS_TYPE=BASIC|PREMIUM
SOURCE_GUIDE
SOURCE_VERSION
RECOMMENDED_USE_CASE
IMAGE_OR_VIDEO_SPEC
MOBILE_LAYOUT
DESKTOP_LAYOUT
CHARACTER_LIMITS
FIELDS_OR_STRUCTURE
SOURCE_NOTES
CURRENT_AVAILABILITY
CURRENT_POLICY_STATUS
VERIFIED_DATE
```

其中 `CURRENT_AVAILABILITY / CURRENT_POLICY_STATUS / VERIFIED_DATE` 必须在运行时更新；PDF 未提供的字段不得推断为官方事实。

---

### 6A.2 BASIC A+｜17 个 Standard 模块完整内置

**SOURCE_SCOPE**：仅 PC 端。模块名称与顺序按 Seller Central 当前 “Add Module” 界面；最低图片尺寸、图片 Alt Text 上限与文本字段字符上限按该指南引用的 Amazon 官方 SP-API A+ Content Examples。

#### BASIC-01｜Standard Company Logo｜标准公司徽标
- `RECOMMENDED_USE_CASE`：Place a clean brand logo at the start or end of the A+ sequence. / Reinforce brand recognition without repeating product claims. / Keep the logo simple enough to remain legible at display size.
- `PC_LAYOUT`：Image minimum `600 × 180 px`。
- `CHARACTER_LIMITS`：Image alt text `≤100`；无 headline/body text 字段。
- `FIELDS_OR_SLOTS`：`1 required image`；Company logo + required image alt text。

#### BASIC-02｜Standard Comparison Chart｜标准比较图
- `RECOMMENDED_USE_CASE`：Compare products within the same brand/catalog. / Clarify size, material, feature, or use-case differences. / Support cross-sell and correct product selection.
- `PC_LAYOUT`：Optional product image，minimum `150 × 300 px`。
- `CHARACTER_LIMITS`：Metric name `≤100`；product title `≤80`；ASIN `≤10`；image alt text `≤100`；metric text `≤250`。
- `FIELDS_OR_SLOTS`：Up to `6 product columns`；Product title/ASIN、optional image、highlight flag、metric rows、metric values。

#### BASIC-03｜Standard Four Image & Text｜标准四图与文本
- `RECOMMENDED_USE_CASE`：Present four benefits, features, steps, or use cases in parallel. / Use when each point needs equal visual weight. / Keep all four images stylistically consistent.
- `PC_LAYOUT`：Each image minimum `220 × 200 px`，共 4 图。
- `CHARACTER_LIMITS`：Main headline `≤200`；each block headline `≤160`；each block body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`4 required images`；Main headline + 4 image/headline/body blocks。

#### BASIC-04｜Standard Four Image/Text Quadrant｜标准四图/文本象限
- `RECOMMENDED_USE_CASE`：Explain four compact feature → benefit pairs. / Use when text needs more space than in a four-column strip. / Best for simple images or icons that remain clear at small size.
- `PC_LAYOUT`：Each image minimum `135 × 135 px`，共 4 图。
- `CHARACTER_LIMITS`：Each quadrant headline `≤160`；body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`4 required images`；4 image/headline/body quadrants。

#### BASIC-05｜Standard Image & Dark Text Overlay｜标准图片 + 深色文字叠加
- `RECOMMENDED_USE_CASE`：Create a wide lifestyle or feature banner. / Use a bright/open image where a dark text box remains readable. / Reserve enough negative space for the overlay.
- `PC_LAYOUT`：Image minimum `970 × 300 px`。
- `CHARACTER_LIMITS`：Headline `≤70`；body `≤300`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required background image`；DARK overlay color + optional headline/body。

#### BASIC-06｜Standard Image & Light Text Overlay｜标准图片 + 浅色文字叠加
- `RECOMMENDED_USE_CASE`：Create a wide lifestyle or feature banner. / Use a darker image where a light text box has strong contrast. / Keep critical product details outside the overlay zone.
- `PC_LAYOUT`：Image minimum `970 × 300 px`。
- `CHARACTER_LIMITS`：Headline `≤70`；body `≤300`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required background image`；LIGHT overlay color + optional headline/body。

#### BASIC-07｜Standard Image Header With Text｜标准图片标题 + 文本
- `RECOMMENDED_USE_CASE`：Lead with a high-impact hero or lifestyle image. / Explain a primary value proposition with more visual depth than an overlay banner. / Use as a strong opening or section break.
- `PC_LAYOUT`：Image minimum `970 × 600 px`。
- `CHARACTER_LIMITS`：Headline `≤150`；subheadline `≤150`；body `≤6000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；Headline + subheadline/body block + image。

#### BASIC-08｜Standard Multiple Image Module A｜标准多图片模块 A
- `RECOMMENDED_USE_CASE`：Show several angles, use cases, variants, or details without stacking multiple modules. / Let shoppers inspect related visual states in one content block. / Keep the sequence coherent rather than mixing unrelated imagery.
- `PC_LAYOUT`：Image minimum `300 × 300 px per block`。
- `CHARACTER_LIMITS`：Each block headline `≤160`；description `≤1000`；caption `≤200`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：Image/text blocks；each block contains image、optional headline、description、caption；thumbnail is generated from the highlight image。

#### BASIC-09｜Standard Product Description Text｜标准产品描述文本
- `RECOMMENDED_USE_CASE`：Add extended explanation, instructions, background, or contextual product information. / Use when the content does not require another visual asset. / Structure copy for scanning rather than creating a dense text wall.
- `PC_LAYOUT`：No image。
- `CHARACTER_LIMITS`：Body text `≤6000`；无 headline field。
- `FIELDS_OR_SLOTS`：`0 image slots`；Body-text-only module。

#### BASIC-10｜Standard Single Image & Highlights｜标准单图与亮点
- `RECOMMENDED_USE_CASE`：Summarize a major feature with supporting sub-points. / Pair one strong visual with compact structured benefits. / Use when bullets improve scanability.
- `PC_LAYOUT`：Image minimum `300 × 300 px`。
- `CHARACTER_LIMITS`：Headline description `≤160`；subheadlines `≤200`；body 1 `≤1000`；bodies 2–3 `≤400`；tech-spec headline `≤160`；bullet text `≤100`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；Headline/description blocks + tech-spec headline + `1–8 bullet positions`。

#### BASIC-11｜Standard Single Image & Sidebar｜标准单图与侧边栏
- `RECOMMENDED_USE_CASE`：Combine a primary story with a secondary proof point or context block. / Separate “what it is” from “why it matters” inside one module. / Use the sidebar for complementary information, not repetition.
- `PC_LAYOUT`：Main image minimum `300 × 400 px`；sidebar image minimum `300 × 175 px`。
- `CHARACTER_LIMITS`：Main headline `≤160`；main subheadline `≤200`；main body `≤500`；main bullets `≤200`；caption `≤200`；sidebar headline `≤200`；sidebar body `≤500`；sidebar bullets `≤200`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`2 required images`；Main image/caption area + sidebar image/text area，含 headline/body/list fields。

#### BASIC-12｜Standard Single Image & Specs Detail｜标准单图与规格详情
- `RECOMMENDED_USE_CASE`：Explain detailed features, compatibility, setup, or product specifications. / Combine one product image with structured technical content. / Useful for reducing fit/specification uncertainty.
- `PC_LAYOUT`：Image minimum `300 × 300 px`。
- `CHARACTER_LIMITS`：Headline `≤200`；description headline `≤160`；description subheadline `≤200`；description body `≤400`；tech-spec headline `≤160`；tech-spec subheadline/bullets `≤200`；tech-spec body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；Description fields + specification fields，含 `1–8 bullet positions` 与 specification text block。

#### BASIC-13｜Standard Single Left Image｜标准左侧单图
- `RECOMMENDED_USE_CASE`：Build a simple feature → benefit narrative with image first. / Alternate with the right-image module to create visual rhythm. / Highlight a close-up, application, material, or result.
- `PC_LAYOUT`：Image minimum `300 × 300 px`。
- `CHARACTER_LIMITS`：Main headline `≤160`；main body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；`imagePositionType=LEFT` + headline/body block。

#### BASIC-14｜Standard Single Right Image｜标准右侧单图
- `RECOMMENDED_USE_CASE`：Continue an alternating left/right content sequence. / Give copy more prominence while retaining one supporting image. / Explain a second feature, use case, or objection.
- `PC_LAYOUT`：Image minimum `300 × 300 px`。
- `CHARACTER_LIMITS`：Main headline `≤160`；main body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`1 required image`；`imagePositionType=RIGHT` + headline/body block。

#### BASIC-15｜Standard Technical Specifications｜标准技术规格
- `RECOMMENDED_USE_CASE`：Present dimensional, material, electrical, compatibility, or component facts. / Reduce uncertainty for specification-driven purchases. / Use when exact facts matter more than persuasive imagery.
- `PC_LAYOUT`：No image。
- `CHARACTER_LIMITS`：Main headline `≤80`；spec name `≤30`；spec definition `≤500`；`4–16 specification rows`。
- `FIELDS_OR_SLOTS`：`0 image slots`；`4–16 specification rows`；`tableCount=1 or 2`。

#### BASIC-16｜Standard Text｜标准文本
- `RECOMMENDED_USE_CASE`：Add a concise transition, brand statement, instruction, or explanation. / Provide context that does not justify another image asset. / Use between visual modules when a short text bridge improves comprehension.
- `PC_LAYOUT`：No image。
- `CHARACTER_LIMITS`：Headline `≤160`；body text `≤5000`。
- `FIELDS_OR_SLOTS`：`0 image slots`；Optional headline + optional body text。

#### BASIC-17｜Standard Three Images & Text｜标准三图与文本
- `RECOMMENDED_USE_CASE`：Show three primary benefits, use cases, steps, or product details. / Create a balanced feature row with strong visual weight per item. / Use when three concepts form a clear, memorable set.
- `PC_LAYOUT`：Each image minimum `300 × 300 px`，共 3 图。
- `CHARACTER_LIMITS`：Main headline `≤200`；each block headline `≤160`；body `≤1000`；image alt text `≤100`。
- `FIELDS_OR_SLOTS`：`3 required images`；Main headline + 3 required image/headline/body blocks。

---
