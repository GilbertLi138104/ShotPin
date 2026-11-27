# 📸 ShotPin拍点

<div align="center">
  <img src="https://img.shields.io/badge/Status-Live-success" alt="Status">
  <img src="https://img.shields.io/badge/Version-1.0-blue" alt="Version">
  <img src="https://img.shields.io/badge/Tech-Vanilla%20JS%20%7C%20Supabase%20%7C%20AMap-orange" alt="Tech">
  
  <p><strong>🌐 <a href="https://www.shotpin.cc" target="_blank">在线体验 Live Demo: www.shotpin.cc</a></strong></p>
</div>

> **A photo-spot sharing and mapping tool for photographers.** Features auto EXIF extraction, AMap location matching, draggable coordinate pinning, map clustering, and a complete cloud-based account and social system. 
>
> **一款为摄影师打造的机位分享与打卡工具。** 支持自动读取照片 EXIF 参数、高德地图精准定位、拖拽反查地名、机位聚合展示以及云端账户与社交互动。

---

## 💡 缘起与痛点 (Background)

在摄影社区里，照片和拍摄信息往往是分离的。看到一张绝美的城市夜景，你可能会在评论区问“求机位”，而作者通常只能回复“在某某桥附近”。因为平台压缩了图片，抹去了 EXIF 参数，机位的准确性、焦段、拍摄时间往往无从考证，导致后来者只能去现场反复试错。

**ShotPin拍点** 解决的正是这个问题：**把“照片、参数、坐标、内容”放进同一个记录动作里。** 用户上传一次，结构化信息同时产生，后面的人可以直接在地图上复现。目标用户不仅是“看照片”的人，而是有明确“去拍”意图的城市风光爱好者、异地拍摄者和内容创作者。

## ✨ 核心功能 (Features)

- **📸 自动解析**：上传照片，系统自动读取相机、镜头、焦段、光圈、快门、ISO、时间和 GPS 定位。
- **📍 地图联动**：如果照片没有定位，用户可通过地图拖拽图钉或搜索地点补全；拖动图钉，自动反查并填入拍摄地点。
- **🗺️ 聚合探索**：在城市密集区域，机位以聚合数字展示防遮挡；放大后散开为照片缩略图。点击信息窗可直接查看参数。
- **🔐 账户体系**：完整的注册、登录、找回密码、注销账号流程。
- **💬 社交互动**：支持对机位进行点赞、评论、收藏，并拥有完整的通知机制。

## 🛠️ 技术架构 (Tech Stack)

这个项目以 **单文件（Single-file）** 形式交付，约 9,000 行原生代码，无框架依赖，极致轻量。
- **前端**：原生 HTML / CSS / JavaScript，无构建工具。
- **地图服务**：高德地图 JS API (包含自研防遮挡聚合算法)。
- **后端与存储**：Supabase (PostgreSQL 数据库、Auth 账户系统、RLS 行级权限控制、云存储)。
- **部署与托管**：Cloudflare Pages (静态托管、全球 CDN 加速) + Porkbun 域名。

## 🧠 项目反思与取舍 (Reflections)

1. **先收敛再扩展**：第一版主动砍掉了关注、私信、评分等“看起来应该有”的功能，集中精力跑通“记录—发现—沉淀”的核心链路。
2. **安全边界在数据库**：坚决使用 Supabase 的 RLS（行级安全策略），确保用户只能修改自己的数据，前端隐藏按钮只是体验，底层安全在数据库。
3. **为体验接受实现复杂度**：放弃现成的聚合插件，自研“矩形重叠判断+同省校验”的聚合逻辑，彻底解决图钉漂移和互相遮挡的问题。
4. **AI 辅助，但不外包判断**：全程借助 AI 编程工具（Cursor / DeepSeek Harness）实现代码，但大量时间花在定义问题、复现 Bug 和验证结果上。AI 提高了实现速度，但产品取舍和判断力仍由人主导。

## 🚀 未来规划 (Roadmap)

- [ ] 拆分单文件代码，引入模块化打包工具。
- [ ] 缩略图剥离数据库，全面迁移至云存储以支持原图查看。
- [ ] 引入内容审核和举报机制，防范公共内容风险。
- [ ] 增加用户行为埋点与错误监控，精准定位用户流失环节。

---
*Created by [GilbertLi138104](https://github.com/Gilbertli). 本项目完整走过了从需求定义、产品设计、数据建模、前端开发到云端部署的全流程。*
