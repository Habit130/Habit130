# habit130 GitHub Profile

## Repository responsibility

构建 habit130 的 GitHub Profile README 与相关静态素材。
参考开源模板和设计，结合 habit 确认的公开个人内容与偏好。
工作区创建分类为 tool；实际交付对象是 GitHub 个人主页内容。

治理事实与任务边界记录在 AGENTS 和 docs；
GitHub issue 是唯一验收合同正文。

## Non-goals

- 不部署独立网站。
- 不默认引入动态生成、外部服务或定时更新。
- 不公开未经 habit 确认的个人信息。
- 不在 Profile README 展示内部交付协议或 handoff。

## Related repositories

主页精选三个项目组，顺序固定；关联仓库只作为公开内容来源，
不属于本仓库的修改范围：

1. LLM-assisted input exploration：
   [Habit130/squirrel](https://github.com/Habit130/squirrel) 与
   [Habit130/librime-llm-rerank](https://github.com/Habit130/librime-llm-rerank)，
   基于上游 Rime/Squirrel 的实验性上下文候选重排序探索。
2. CV research practice：
   [Habit130/cv-research-practice](https://github.com/Habit130/cv-research-practice)，
   建设中的科研实践 scaffold，覆盖论文选读、复现、实验记录与对比、报告。
3. CropGuard：位于
   [Habit130/MiniGPT-4](https://github.com/Habit130/MiniGPT-4)，
   基于 MiniGPT-v2 的作物图像 visual question answering 应用，非专业诊断。

项目介绍以相应公开 README 为依据；文档描述不等于独立运行或性能验证。
展示关联项目不意味着原创上游软件、论文或模型。
父级 Projects 工作区基础设施不属于本仓库修改范围。

## Language

- GitHub Profile README: 根 `README.md` 为英文默认版，由 GitHub 在个人主页展示；
  `README.zh-CN.md` 为等价简体中文版，保留 English 项目与专业术语，双向切换。
- Public identity: 仅使用 Habit、已确认的兴趣驱动探索与 AI 辅助实践、精选项目；
  不推断或公开职业、履历、联系方式或个人生活信息。
- Static assets: `assets/profile/` 下的原创静态向量字标与低高度页头，
  使用 light/dark treatment 和 fallback，不依赖外部字体或图片服务。
- Governance: 仓库协作边界、任务合同、验证及交付协议，
  与主页展示内容分离。
