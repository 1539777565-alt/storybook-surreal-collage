---
name: storybook-surreal-collage
description: 把照片变成童话绘本感的超现实剪纸拼贴(storybook surreal collage)——人物、前景和未编辑区域默认保留原始自然色与摄影质感，用分层平涂色形、剪纸云带、手绘涂鸦和一个"不可能的巨物"重塑背景。当用户想要童话异想拼贴、绘本式照片改造、明亮梦境海报、剪纸天空、原色照片+柔和平涂色块，或需要只改天空/背景的局部超现实编辑时使用。
---

# 童话异想拼贴 Storybook Surreal Collage

**真实留色、平涂梦境、一物不对劲、元素源于图、色从图中来。**

照片还是那张照片，但世界被换掉了：人物、前景和未编辑区域以原始自然色与摄影质感保留为"现实锚"，背景由 2–3 组巨大平涂色形组织成前后层次，全图只有**一个**不可能的巨物——超现实的全部力量在于"只有一处不对劲"。

## 决策优先级(冲突时按此顺序)

1. 锚点可识别——3 秒内认出原图主体；身份、原始自然色与摄影纹理优先保留，脸部核心区不许压元素
2. **只有一个不对劲**——巨物唯一；出现第二个不可能元素就删
3. 元素源于场景——巨物和色形都要能从原图/场景典故里指出处
4. 平涂纪律——平涂只进入改造区域；色形无渐变、无立体阴影，这是和原色照片真实感对撞的关键
5. 明亮度——整体保持亮，禁止暗黑恐怖

## 授权与隐私

- 用户给了照片并要求生成/改造，即视为已授权调用生图服务，不再追问
- 只把最终 prompt 和参考图发给生图服务；不传播、不另存用户原图

## 第一步：场景卡

读原图，逐项写下：

- **锚点主体**：最有识别度的主体(人/物/景)，位置与占比
- **区域边界**：天空/地面/水面/墙面等可被平涂替换的区域
- **原生色**：2–3 个主色(色形颜色的来源)
- **主导动势**：最强方向线(对角/纵深/视线)
- **场景典故**：若为文化地标，它最出名的一句话知识(巨物的首选来源)

## 第二步：色形推导(禁止默认红日蓝天)

### 现实锚的色彩规则

- 默认保留人物、前景、服装、地景和所有未编辑区域的原始自然色与摄影纹理，不做全局去色。
- 可以轻微统一曝光或降低过强杂色，但不得把现实锚变成黑白、灰阶或单色。只有用户明确要求黑白效果时才允许去色。
- 平涂色形只进入天空、海面、墙面或用户指定的背景区域；边界外写明 `keep the exact original natural colors`。
- 拼贴冲突来自「真实摄影纹理 vs. 平涂剪纸色形」，不依赖「黑白 vs. 彩色」。

- **形状**：圆(日/月)、拱、地平线色块、整面天空，选 2–3 组，贴合场景原有区域边界
- **颜色三选一策略**：①场景已有色提纯(草绿→翠绿) ②互补色对撞(暖橙场景→群青) ③情绪反转色(阴郁场景→明黄)
- 平涂无渐变

### 天空是主要改造区时：首轮就做出层次

除非用户明确要极简/留白，天空不能只是「一整块底色 + 巨物 + 鸟」。在第一次生成就分配 3 个视觉层次：

1. **远层**：一片安静的大底色，保留约 25–40% 无装饰呼吸区。
2. **中层**：1 组横向或斜向延展的剪纸云带/波浪带；可由同色深浅的 1–2 条嵌套轮廓组成，算同一色形组。
3. **近层**：贴着山脊、建筑或海平线的色带/云团，承担地景与天空的衔接。

- 巨物是焦点，不替代中层；把巨物放在空区的一侧，另一侧至少要有云带、鸟群或线条回应它。
- 装饰预算：鸟群 3–5 只沿一条弧线；白色涂鸦 2–3 条；星点/雪花状小涂鸦 3–5 个为一小组。它们补节奏，不可取代色形层次。
- 色带必须来自场景色：海/天空可推出蓝灰、雾紫；日落/木屋/杯子可推暖杏、奶油黄、珊瑚；帽子或衣物的图案色可用于焦点呼应。禁止无来源地套用彩虹。
- 眯眼检查：上半部若只读成一片平蓝，说明层次不足；新增一条中层色带或一组小涂鸦，而不是新增第二个巨物。

### 局部编辑模式

当用户说「只改天空」「局部处理」或给出明确边界时，现实锚包括所有未指定区域：在 prompt 中先写 `change only [区域]`，再逐项锁定人物、地景、建筑、水面、手部、构图、纹理与原始自然色。重复要求干净的山脊/屋顶/树枝边缘；不要使用会暗示整图风格迁移或全局去色的措辞。若首次结果越界，只允许一次针对越界区域的纠偏重生成。

## 第三步：巨物选择(禁止默认海豚鲸鱼)

按优先级选**一个**：

0. **典故巨物(文化地标首选)**：从景点最出名的典故里选，但先翻译成"可见的物件或动作"——运石→船队拖石、渔隐→巨网罩园、贴水→离水漂浮、以壁为纸→真山从纸里晕出、碑刻→刻线流成真河。只取大众记忆点(3 秒要懂)。自检：能写出"白居易的灯笼升成月亮"这种一句话配文才算焊上
1. **场景元素荒诞化**：把图里已有的小东西放大到不合常理(咖啡杯大过楼房)
2. **语义最远物**：和场景距离最远的东西(沙漠里游泳的人)
3. **尺度颠倒**：人小物大或反之

## 第四步：小元素与涂鸦

- 成群小元素(飞鸟/落叶/纸船)3–5 个，大小梯度 100/60/30，沿一条弧线分布
- 白色手绘涂鸦线条 2–3 条(刷痕/波浪线/星星)，做手工痕迹
- 禁止孤立单个装饰

## Prompt 编译器(四段式)

只写能变成像素的指令：

1. **风格定位**：`storybook surreal collage, preserve the original composition and orientation`
2. **现实锚**：`keep the [主体、前景与未编辑区域] clearly recognizable and photorealistic in their exact original natural colors, preserving identity, texture and lighting; do not desaturate`
3. **平涂世界与巨物**：`the [区域] replaced by three visual layers of huge flat matte color-shape groups: [远层底色], [中层嵌套云带], [近层地平线/边界色带], one impossible giant element: [巨物，按选择规则], flat matte colors, no gradients`
4. **小元素与约束**：`[小元素群] in graduated sizes following an arc, a small grouped cluster of star/snowflake doodles, 2–3 white hand-drawn graffiti strokes, keep 25–40% of the sky quiet, keep all foreground and unedited photo regions in their exact original natural colors, [局部模式时写明所有锁定区域], no text, no watermark`

**范例**(纽约街景)：`storybook surreal collage, keep the people, buildings and street photorealistic in their exact original natural colors; do not desaturate, replace only the sky with a quiet lemon-yellow far layer purified from the taxis, one nested cream cut-paper cloud band and one brick-red near-horizon band, one impossible giant element: a giant traffic light hanging between the towers like a chandelier, a flock of small pigeons in graduated sizes following an arc, a few white hand-drawn graffiti strokes, flat matte colors only in the edited sky, no gradients, no text, no watermark`

## 纠偏(最多重生成一次，只修观察到的失败)

- **装饰和场景两张皮** → 检查每个元素是否写明源形关系(extend into / becomes / continues as)
- **太满/发闷** → 删一组元素，加大平涂安静区
- **巨物超过一个** → 删到只剩一个
- **渐变/立体阴影** → 加 `flat matte colors, no gradients, no shadows on the color shapes`
- **天空太空、像底色加贴纸** → 保留巨物不加第二个；补一组横贯上/中景的嵌套云带，再加一小组星点或雪花状涂鸦
- **人物或下半部变黑白** → 恢复人物、服装、前景和未编辑区域的原始自然色；在下一次只重申 `do not desaturate` 与色彩边界，不改变其他设计
- **局部编辑污染地景** → 下一次只重申编辑区域和边缘遮罩，逐项锁定所有未编辑主体；不要再叠加新的风格要求
- **照搬参考图元素(红日/海豚/鲸鱼)** → 重做事先走色形推导和巨物选择，照抄即抄袭
- **文字乱码** → 中文移出 prompt 改后期代码排；英文单词保持 4–6 字母

## 硬禁忌

第二个不可能的巨物；默认全图去色或把前景变成黑白；色形渐变；立体阴影；进口素材；暗黑恐怖基调；装饰压脸；相框式整圈包围；满版纹理覆盖；中文文字进 prompt(必乱码，后期排)；水印。

## 质量门(交付前逐项过)

- 3 秒内认出锚点？
- **全图只有一个"不对劲"？**
- 巨物能说出出处(场景元素/典故)？
- 色形颜色能从原图主色指出处？
- 平涂无渐变、无明暗立体？
- 天空作为主背景时，远/中/近三层是否都可读，且未把上半部留成无意图的大空块？
- 小元素成群有梯度、沿弧线？
- 人物、前景和未编辑区域是否保留原始自然色，没有意外灰阶化？
- 眯眼看：画面明亮，原色摄影现实与平涂剪纸梦境的对撞是否清晰？

## 输出格式

默认只返回：生成的图 + 1–3 句创作思路(说清色形推导和巨物出处，不暴露完整 prompt)。用户明确要求时才附 prompt。
