# MCP 科普视频 — Expanded Production Breakdown

## Style & Palette
- **Mood**: Dark/premium tech — cinematic, clean, authoritative. Think Apple keynote meets 科普动画.
- **Palette** (from Dark Premium):
  - `#0A0E1A` — background (very dark navy)
  - `#14213D` — surface/card
  - `#1D3557` — surface alt
  - `#4A7DFF` — primary accent (bright blue)
  - `#7C5CFC` — secondary accent (purple)
  - `#00D4AA` — teal accent (success/connection)
  - `#FFFFFF` — text primary
  - `#8892B0` — text secondary
  - `#3D4A6B` — text muted / decorative lines
- **Typography**: 
  - `"Space Grotesk", sans-serif` — English display (MCP, labels, numbers)
  - `"PingFang SC", "Microsoft YaHei", sans-serif` — Chinese body text
- **Format**: 1080×1920 vertical (抖音/B站短视频)
- **Duration**: ~46 seconds

## Rhythm
```
hook → PROBLEM → ANALOGY → ARCHITECTURE → FLOW → APPLICATIONS → CTA
```

## Global Rules
- **Transitions**: Crossfade between all scenes (0.5s, power2.inOut). Educational pacing — smooth and continuous.
- **Background**: Persistent subtle tech grid pattern across all scenes. Radial accent glows shift position per scene.
- **Decorative motif**: Animated connection lines/dots motif representing "protocol/connection" — appears in BG of every scene.
- **Motion style**: Medium energy — slides, fades, draws. No aggressive slams. Professional explainer tone.
- **Scene structure**: Build (30%) → Breathe (50%) → Resolve (20%)

## Scene Beats

### Scene 1: Hook — "什么是 MCP？" (0s → 4s, hold 4s)
- **Concept**: Open on deep space-like navy canvas. A glowing grid recedes into the distance. Ghost text "MCP" sits massive and faint in the background. The title "什么是 MCP？" SLAMS in — this is the question everyone asks.
- **Depth layers**:
  - BG: Tech grid pattern (CSS), faint radial blue glow centered, ghost "MCP" at 5% opacity, 300px
  - MG: Title "什么是 MCP？" 120px bold white, subtitle "Model Context Protocol" 42px secondary
  - FG: Accent bar under title (4px, #4A7DFF), tagline "AI 领域的 USB 接口" in teal
- **Choreography**:
  - t+0.2: Grid fades in (1.5s slow breath)
  - t+0.5: Title SLAMS from y:30, opacity:0 — expo.out, 0.6s
  - t+0.8: Accent bar draws scaleX 0→1 — power2.out, 0.4s
  - t+1.0: Subtitle fades in — power2.out, 0.5s
  - t+1.3: Tagline slides from left, letter-spacing opens — power3.out, 0.5s
- **Ambient**: Grid lines pulse scale 1↔1.02 over 3s
- **Transition**: Crossfade to S2 at 3.5s

### Scene 2: Problem — "AI 接入数据的四大痛点" (4s → 9.5s, hold 5.5s)
- **Concept**: The "before" state. Four pain points displayed as cards in a 2×2 grid, each with a stark X icon. The message: current integration is fragmented and painful.
- **Depth layers**:
  - BG: Same grid, shifted radial glow to upper-left
  - MG: Section label "在 MCP 出现之前..." + 4 problem cards
  - FG: Decorative dots, category labels
- **Pain points**:
  1. "各自为战" — 每个 API 单独对接
  2. "重复造轮" — 集成代码反复写
  3. "框架绑架" — 抽象过重学习成本高
  4. "生态孤岛" — 封闭插件难通用
- **Choreography**:
  - t+4.3: Section label slides down from top — power2.out, 0.4s
  - t+4.7: Cards CASCADE in from various directions (L, R, L, R) — stagger 0.15s, power3.out
  - t+5.5: X marks appear on each card with a subtle scale pop
- **Ambient**: Cards breathe slightly (scale 1↔1.01)
- **Transition**: Crossfade to S3 at 9.0s

### Scene 3: Analogy — "MCP = AI 的 USB 接口" (9.5s → 15.5s, hold 6s)
- **Concept**: The "aha" moment. Show the USB metaphor visually: a brain icon on the left, a "USB plug" shape on the right, with a clean connection path between them. The metaphor lands: MCP standardizes AI connections just like USB standardized peripherals.
- **Depth layers**:
  - BG: Grid, warm blue glow centered
  - MG: Brain icon (geometric), connection path, plug icon, "MCP = AI 的 USB 接口" hero text
  - FG: Benefit badges "标准化 · 即插即用 · 通用协议"
- **Choreography**:
  - t+9.8: Brain icon slides from left — power3.out, 0.5s
  - t+10.0: Plug icon slides from right — power3.out, 0.5s
  - t+10.3: Connection path draws (scaleX or SVG draw) — power2.out, 0.6s
  - t+10.8: Hero text fades up — power2.out, 0.5s
  - t+11.3: Benefit badges cascade in from below — stagger 0.1s
- **Ambient**: Connection path pulses opacity 0.6↔1 over 2s
- **Transition**: Crossfade to S4 at 15.0s

### Scene 4: Architecture — "核心架构" (15.5s → 22.5s, hold 7s)
- **Concept**: The architecture diagram. A clean, layered block diagram showing Host → Client → Server → Data sources. Each level reveals sequentially, building the mental model.
- **Depth layers**:
  - BG: Grid, purple-tinted glow at bottom
  - MG: Architecture diagram — layered boxes connected by lines
  - FG: Labels "Host", "Client", "Server", 3 capability badges
- **Diagram layers**:
  - Level 1: "MCP Host" (Claude Desktop / AI工具) — green box
  - Level 2: "MCP Client" (1:1连接) — blue box
  - Level 3: "MCP Server" row — 3 purple boxes (本地/远程/社区)
  - Level 4: Data sources below
  - Side: 3 capability badges (Resources / Tools / Prompts)
- **Choreography**:
  - t+15.8: Title fades in from top
  - t+16.1: Host box drops in — power3.out, 0.4s
  - t+16.5: Connection line draws down — scaleY, 0.3s
  - t+16.7: Client box drops in — power3.out, 0.4s
  - t+17.1: Server row: 3 boxes stagger in — each 0.3s, power2.out
  - t+18.0: Data sources fade in
  - t+18.3: Capability badges stagger from right
- **Ambient**: Boxes have subtle glow pulse
- **Transition**: Crossfade to S5 at 22.0s

### Scene 5: Flow — "一次完整调用" (22.5s → 31.5s, hold 9s)
- **Concept**: A circular flow diagram showing the 6-step MCP call process. Each step is a node with an icon, connected by arrows forming a cycle. The key insight: LLM chooses the tool, not hardcoded.
- **Depth layers**:
  - BG: Grid, wide blue glow
  - MG: Circular/curved flow path with 6 nodes
  - FG: Step labels, directional arrows, small note about system prompt
- **6 nodes**:
  1. 用户提问 — person icon
  2. LLM 推理 — brain icon
  3. 选择工具 — compass icon
  4. 调用执行 — play icon
  5. 结果返回 — return arrow
  6. 生成回答 — chat bubble
- **Choreography**:
  - t+22.8: Title slides in
  - t+23.3: Nodes appear one by one in sequence (stagger 0.4s) — each with a scale pop
  - t+25.5: Arrows draw between nodes
  - t+26.5: Connection lines form the complete cycle
  - t+27.0: Note text fades in "本质是提示工程"
- **Ambient**: The completed cycle pulses gently
- **Transition**: Crossfade to S6 at 31.0s

### Scene 6: Applications — "能做什么？" (31.5s → 38.5s, hold 7s)
- **Concept**: A grid of 4 application categories showing real-world uses. Each category has a gradient background and 2-3 example labels. Shows breadth without overwhelming.
- **Depth layers**:
  - BG: Grid, teal-tinted glow
  - MG: 4 category cards in 2×2 with icons
  - FG: Example labels per category
- **Categories**:
  1. 📁 数据文件 — 文件系统 / 数据库 / Google Drive
  2. 🛠 开发工具 — Git / GitHub / Sentry
  3. 🌐 网络服务 — 搜索 / 浏览器 / Fetch
  4. ⚡ 生产力 — Slack / Google Maps / Memory
- **Choreography**:
  - t+31.8: Title fades in
  - t+32.2: 4 cards fly in from 4 corners — each 0.4s, power3.out
  - t+33.5: Example labels fade in within each card
- **Ambient**: Cards have subtle hover-like elevation
- **Transition**: Crossfade to S7 at 38.0s

### Scene 7: Outro — CTA (38.5s → 46s, hold 7.5s)
- **Concept**: Clean closing. The message "MCP 正在重新定义 AI 的连接方式" centered and powerful. A soft CTA to try it. Final fade to black.
- **Depth layers**:
  - BG: Dark, single centered radial glow, grid fading out
  - MG: Closing statement + CTA button
  - FG: Small dots particle effect
- **Choreography**:
  - t+38.8: Closing statement fades in — power2.out, 0.8s
  - t+40.0: CTA "去 Claude Desktop 体验 →" fades in — power2.out, 0.5s
  - t+44.0: Entire scene fades to black — power2.in, 1.5s
- **Transition**: Fade to black (exit)

## Recurring Motifs
- **Connection lines**: Animated lines/dots appear in every scene's BG as a visual metaphor for "protocol/connection"
- **Grid pattern**: Persistent tech grid anchoring the dark theme
- **Accent transitions**: Each scene's hero element uses the #4A7DFF accent

## Negative Prompt
- No neon overload — keep it professional, not gaming aesthetic
- No gradient text on large headlines (hard to read at video resolution)
- No emoji as primary icons (use simple geometric icons)
- No pure black (#000) — use very dark navy (#0A0E1A) instead
- No complex 3D — flat 2D with depth layers is sufficient
