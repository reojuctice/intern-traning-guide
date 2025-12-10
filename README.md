# 实习生入职前技术储备（2025版）

> 主要方向：C端前端开发 + AI Agent

## 写在前面

这份指南的目的是**指明方向，而不是限制路径**。

我们希望你能：
- **主动探索**：每个人的学习节奏和兴趣点不同，不需要严格按照某个时间表或清单来
- **保持好奇心**：遇到感兴趣的技术可以深入钻研，不要局限于这里列出的内容
- **注重理解**：比起完成多少个任务，更重要的是真正理解背后的原理和思想
- **享受过程**：学习应该是有趣的，不是压力

这里列出的是我们认为重要的技术方向和学习资源，但具体怎么学、学多深，由你自己决定。

---

## 快速开始

看完整个文档可能会觉得内容很多，不知道从哪里开始。这里给你一个简单的上手指南：

### 如果你只有 30 分钟

1. **马上开始**：打开 Cursor，跟着做一个 Next.js 官方教程
2. **理解理念**：看完本文档的"写在前面"和"Code Review 能力"章节
3. **设定目标**：选择 1-2 个感兴趣的方向深入

### 第一周可以做什么

**前端基础（3-4 天）**
- 搭建第一个 Next.js 项目（用 `npx create-next-app@latest`，跟官方教程）
- 体验 React 19 的 Actions（做个简单的表单提交）
- 用 Cursor 写代码，感受 AI 辅助开发
- 让 AI 生成一个组件，然后用 CR 清单审查它

**AI 初体验（2-3 天）**
- 用 Claude/GPT 解决学习中的问题
- 部署运行 Browser-Use（10 分钟就能体验）
- 观察它怎么理解指令、怎么操作浏览器
- 记录 AI 犯的错误，建立自己的经验库

**建议：先动手，再深入**
- 不要一开始就啃源码和论文
- 先把东西跑起来，有感觉了再看原理
- 遇到不懂的随时问 AI
- 保持学习的乐趣最重要

---

## 一、前端基础

### 1. React 核心原理

**为什么要学原理？**

在 AI 时代，光会用框架是不够的。你得懂原理，才能更好地指挥 AI 干活，也能看出 AI 生成的代码哪里有坑。

**重点掌握：**

**Hooks 原理**
- useState/useEffect 内部怎么实现的，为什么不能在条件语句里用 Hooks
- Fiber 架构和 Hooks 链表结构，理解了这个很多诡异的 bug 就能解释了
- 闭包陷阱怎么产生的，怎么避免

**React 19 新东西（必看）**
- **Actions**：处理异步操作的新方式，比 useEffect + useState 那套优雅多了
  - 自动处理 loading、error 状态
  - 表单提交、数据更新这些场景特别好用
  
- **Server Components**：这个是大趋势，必须搞懂
  - 什么时候用 Server Component，什么时候用 Client Component
  - 数据怎么在服务端和客户端之间流转
  - 和传统 SSR 的区别在哪

- **use() Hook**：新出的 Hook，可以读 Promise 和 Context，简化异步处理

- **View Transitions**：页面切换动画，C 端体验优化的利器

**渲染机制**
- Virtual DOM Diff 算法，key 到底有什么用
- 并发渲染、时间切片，React 18/19 的核心
- useTransition、useDeferredValue 什么时候用

**怎么学？**
- React 官方文档必读，尤其是 React 19 的更新说明
- 找几篇好的源码解析文章，理解 Fiber 和 Hooks
- 自己动手实现一个简易版 useState，加深理解

---

### 2. SSR 相关（Next.js 15/16）

**为什么重要？**

我们这边主要做 C 端业务，大量用 SSR。首屏快、低端机也能跑得动。

**Next.js 15/16 必知必会：**

**App Router**
- 文件系统路由、Layout、Template 这些基础
- 并行路由、拦截路由这些高级用法
- 什么时候用服务端组件，什么时候用客户端组件

**数据获取**
- Server Components 里怎么取数据
- 缓存策略（fetch 缓存、Request Memoization）
- ISR（增量静态再生成）怎么用

**Turbopack（重点）**
- Next.js 16 的默认打包器，用 Rust 写的
- 构建速度提升 2-5 倍，热更新快 10 倍
- 基本用法和配置，跟 Webpack 的区别

**React Compiler**
- 自动帮你做 memoization，不用到处写 useMemo/useCallback
- 理解它的优化策略，知道什么时候还是要手动优化

**缓存机制（Next.js 16 新特性）**
- 四层缓存：Request Memoization、Data Cache、Full Route Cache、Router Cache
- 新的 API：`updateTag()`、`refresh()`
- 怎么控制缓存失效

**性能优化**
- FCP、LCP、TTI 这些指标怎么优化
- 低端机适配（4G 网络 + 低端 CPU）
- Code Splitting、懒加载、Critical CSS
- 流式渲染（Streaming）、选择性水合（Selective Hydration）

**前沿技术（了解即可）**
- MRAH 架构：根据设备能力和网络状况动态调整水合策略
- Islands 架构：只对需要交互的部分进行水合，静态内容零 JS

**怎么学？**
- 跟着 Next.js 官方教程做一遍
- 自己搭 2-3 个项目：博客（SSG）、电商首页（SSR）、Dashboard（混合）
- 用 Lighthouse 跑分，目标 90 分以上
- 模拟低端机环境测试性能

---

### 3. TypeScript

**基础必会：**
- 类型推导、泛型、联合类型、交叉类型

**进阶（重要）：**
- 条件类型、映射类型、模板字面量类型
- 工具类型（Partial、Pick、Omit、Record 这些）

**AI 时代的特殊需求：**
- Zod / Valibot 这种 Schema 验证库必须会
- 确保 AI 生成的数据是类型安全的
- 运行时类型检查，AI 输出不能无脑信任

---

### 4. 工程化基础

**构建工具**
- Vite：理解 ESM 开发模式，为什么这么快
- Webpack：传统但还得懂，Loader 和 Plugin 机制
- Turbopack：未来趋势，Rust 带来的性能提升

**测试**
- Jest/Vitest：单元测试
- Playwright/Cypress：E2E 测试
- 关键路径覆盖就行，不用过度测试

**代码质量**
- ESLint + Prettier，配合 Husky
- Code Review 清单，尤其是审查 AI 代码的要点

---

### 5. Code Review 能力

**为什么 CR 这么重要？**

在 AI 时代，Code Review 的重要性不降反升：
- AI 会犯错，而且有些错误很隐蔽
- 你是代码质量的最后一道防线
- CR 能力直接体现你对技术的理解深度

**通用 CR 清单：**

**功能正确性**
- 满足需求了吗？边界条件处理了吗？
- 错误处理完善吗？异常分支都考虑到了吗？
- 用户输入做校验了吗？

**性能问题**
- React 组件：会不会无限重渲染？依赖数组写对了吗？
- 循环嵌套：O(n²) 甚至 O(n³) 的算法能不能优化？
- 内存泄漏：定时器清了吗？事件监听移除了吗？useEffect 的清理函数写了吗？

**安全漏洞**
- XSS：用户输入有没有做转义？用 dangerouslySetInnerHTML 是不是必要的？
- 敏感信息：API Key、Token 有没有泄漏到前端代码里？
- 依赖安全：第三方包是不是已知有漏洞的版本？

**可维护性**
- 命名清晰吗？看名字能知道这个函数/变量是干什么的吗？
- 结构合理吗？一个函数是不是干了太多事？
- 注释必要吗？（好代码应该自解释，只在必要时加注释）

---

**AI 代码专项审查清单：**

这是重点，AI 生成的代码有一些特有的问题模式。

**1. API 和库的使用**

❌ **常见问题：用了过时的 API**

```typescript
// AI 可能生成这样的代码（React 17 的写法）
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<App />, document.getElementById('root'));
```

✅ **你要检查：是不是 React 18/19 的新写法？**

```typescript
// React 18+ 的正确写法
import { createRoot } from 'react-dom/client';

const root = createRoot(document.getElementById('root')!);
root.render(<App />);
```

**审查要点：**
- 检查 import 语句，确认 API 是当前版本支持的
- 特别注意 React、Next.js 这种更新快的框架
- 遇到不确定的 API，去官方文档确认一下

---

**2. 虚构函数和库（Hallucination）**

❌ **AI 可能编造不存在的函数**

```typescript
// 这个 useOptimizedState 并不存在
import { useOptimizedState } from 'react';

function MyComponent() {
  const [count, setCount] = useOptimizedState(0);
  // ...
}
```

✅ **审查要点：**
- 看到没见过的 Hook 或函数，先去文档查一下
- 检查 import 的包是不是真实存在的
- 如果是自定义 Hook，确认项目里是不是真的有

**快速验证方法：**
- 在 IDE 里跳转到定义，跳不过去就可能是编造的
- 去 npm 或官方文档搜索一下

---

**3. 边界条件和错误处理**

❌ **AI 经常忽略边界情况**

```typescript
function getUserName(user: User) {
  return user.profile.name; // 如果 profile 是 null 呢？
}

// 使用的时候
<div>{getUserName(currentUser)}</div> // currentUser 可能是 undefined
```

✅ **正确的处理**

```typescript
function getUserName(user: User | undefined) {
  return user?.profile?.name ?? '匿名用户';
}

// 或者在使用时判断
{currentUser && <div>{getUserName(currentUser)}</div>}
```

**审查要点：**
- 所有的对象访问，想想如果是 null/undefined 会怎样
- 数组操作，空数组的情况处理了吗？
- API 调用，失败了怎么办？loading 状态呢？

---

**4. React Hooks 的依赖数组**

❌ **AI 经常漏掉依赖或者加错依赖**

```typescript
function SearchComponent() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState([]);

  useEffect(() => {
    fetchResults(query).then(setResults);
  }, []); // ❌ 少了 query 依赖，query 变化不会重新搜索
}
```

✅ **正确的写法**

```typescript
useEffect(() => {
  fetchResults(query).then(setResults);
}, [query]); // ✅ 加上 query 依赖
```

**审查要点：**
- useEffect/useCallback/useMemo 的依赖数组仔细检查
- ESLint 的 exhaustive-deps 规则必须开启
- 如果真的需要空依赖数组，想想是不是应该用 useRef

---

**5. 性能问题**

❌ **AI 可能写出性能很差的代码**

```typescript
function ProductList({ products }) {
  return (
    <div>
      {products.map(product => (
        // ❌ 每次渲染都创建新函数，子组件会无限重渲染
        <ProductCard 
          key={product.id} 
          product={product}
          onDelete={() => deleteProduct(product.id)}
        />
      ))}
    </div>
  );
}
```

✅ **优化后**

```typescript
function ProductList({ products }) {
  const handleDelete = useCallback((id: string) => {
    deleteProduct(id);
  }, []);

  return (
    <div>
      {products.map(product => (
        <ProductCard 
          key={product.id} 
          product={product}
          onDelete={handleDelete}
          productId={product.id}
        />
      ))}
    </div>
  );
}

// ProductCard 要用 memo 包裹
const ProductCard = memo(({ product, onDelete, productId }) => {
  return (
    <div>
      {product.name}
      <button onClick={() => onDelete(productId)}>删除</button>
    </div>
  );
});
```

**审查要点：**
- map 里创建函数要小心，看看能不能提到外面
- 大列表考虑虚拟滚动（react-window）
- 复杂计算用 useMemo 缓存

---

**6. TypeScript 类型安全**

❌ **AI 可能用 any 逃避类型检查**

```typescript
function processData(data: any) { // ❌ any 类型失去了类型保护
  return data.map((item: any) => ({
    id: item.id,
    name: item.name.toUpperCase(),
  }));
}
```

✅ **正确的类型定义**

```typescript
interface DataItem {
  id: string;
  name: string;
}

function processData(data: DataItem[]) {
  return data.map(item => ({
    id: item.id,
    name: item.name.toUpperCase(),
  }));
}
```

**审查要点：**
- 禁止 any，除非真的没办法
- unknown 比 any 安全，需要类型收窄
- 用 Zod 之类的库做运行时校验（特别是 AI 返回的数据）

---

**7. 副作用和纯函数**

❌ **AI 可能写出有副作用的代码**

```typescript
function calculateTotal(items: Item[]) {
  let total = 0;
  items.forEach(item => {
    item.processed = true; // ❌ 修改了输入参数！
    total += item.price;
  });
  return total;
}
```

✅ **纯函数，无副作用**

```typescript
function calculateTotal(items: Item[]): number {
  return items.reduce((sum, item) => sum + item.price, 0);
}

// 如果需要标记 processed，返回新对象
function markItemsProcessed(items: Item[]): Item[] {
  return items.map(item => ({ ...item, processed: true }));
}
```

**审查要点：**
- 函数不应该修改输入参数
- 工具函数应该是纯函数
- React 组件渲染期间不能有副作用

---

**实用技巧：**

**建立自己的 Checklist**
- 每次发现 AI 的新坑，记录下来
- 做成清单，每次 CR 过一遍
- 团队共享，大家都能避坑

**使用工具辅助**
- ESLint + TypeScript：自动检查很多问题
- SonarQube：代码质量扫描
- Lighthouse：性能检查
- 但工具不是万能的，人工审查不可替代

**不要无脑接受 AI 的建议**
- 看到 AI 生成的代码，第一反应应该是"这样对吗"而不是"太好了"
- 每一行都要理解为什么这样写
- 不理解的代码不要合并

**学会质疑**
- "这个函数真的需要这么复杂吗？"
- "有没有更简单的实现方式？"
- "这样写会不会有性能问题？"
- "边界情况都考虑到了吗？"

---

## 二、AI Agent 开发

### 1. Prompt Engineering

**基础模式：**

**Few-shot Learning**
- 给几个例子，让模型学会你要的模式
- 例子选得好不好，直接影响效果
- 可以从向量库里动态检索最相关的例子

**Chain-of-Thought（思维链）**
- 让模型一步步推理，不要直接给答案
- 数学题、逻辑分析这种特别有用

**ReAct（推理+行动）**
- 经典模式：推理 → 行动 → 观察 → 再推理
- 工具调用的基础
- 要设计好错误处理和重试逻辑

**结构化输出）**
- OpenAI 的 Structured Outputs：100% 保证 JSON 格式正确
- Function Calling：让 LLM 调用你的工具
- 一定要做参数校验，AI 有时候会瞎传参数

**上下文管理：**

这个很重要，复杂任务上下文容易爆

**滑动窗口**
- 保留最近 N 轮对话
- 重要信息（比如任务目标）要一直保留
- 不重要的中间过程可以丢弃

**上下文压缩**
- LongLLMLingua：智能压缩算法，能省不少 Token
- 关键信息提取和摘要
- 压缩率和质量之间要权衡

**RAG（检索增强）**
- 向量数据库（Pinecone、Qdrant）存长期知识
- 需要的时候检索出来
- 检索策略：相似度阈值、Top-K、Reranking

**浏览器自动化场景的 Prompt：**

**DOM 描述**
- HTML 太长了，要简化，只保留关键信息
- 用 Accessibility Tree，比完整 DOM 简洁
- 元素定位：CSS Selector、文本匹配、视觉位置

**操作指令**
- 定义好原子操作：click、type、scroll、wait
- 复杂操作分解成步骤
- 错误处理：元素没找到怎么办、操作失败怎么重试

**参考项目：**
- **Browser-Use**：看它怎么简化 DOM，怎么生成操作序列
- **Skyvern**：工作流编排，多步骤任务的上下文管理
- **Stagehand**：元素定位，截图 + Vision 模型

**实践建议：**
- 对比不同模型的效果：
  - 国际主流：GPT-5、Claude 4.5 Sonnet、Gemini 3 Pro
  - 国产优秀：Qwen-Max (3)、DeepSeek-V3
- 建立 Prompt 版本管理，A/B 测试


---

### 2. Agent 架构

**基础概念：**

**Agent Loop**
- 感知：获取环境状态（DOM、API 返回、截图等）
- 决策：分析任务，选择策略，生成计划
- 执行：调用工具，完成操作
- 循环：根据结果调整计划

**错误处理**
- 分类：可恢复（重试）vs 不可恢复（放弃）
- 重试策略：指数退避，最多重试 3 次
- 降级方案：简化版功能或人工介入

**状态管理**
- 短期记忆：当前任务的上下文
- 长期记忆：历史经验、知识库
- 工作记忆：正在处理的中间结果

**现代架构（重点）：**

**RA-Gen **
- 针对代码生成场景
- 多 Agent 协作：Coordinator（协调）、Executor（执行）、Verifier（验证）
- 提升安全性、准确性、可控性
- 论文：arXiv:2510.08665

**Planner-Centric（规划器中心）**
- 比简单 ReAct 更适合复杂任务
- 全局规划器：一开始就规划好整体方案
- 层次化分解：大任务拆成子任务
- 动态调整：执行中可以改计划
- 论文：Beyond ReAct（arXiv:2511.10037）

**MCP（Model Context Protocol）**
- Anthropic 推的标准协议
- 统一工具调用接口，跨平台共享
- 降低集成成本

**Tools 设计：**

**规范化**
- JSON Schema 定义输入输出
- 参数必须做校验（类型、范围、格式）
- 错误信息要清晰，告诉 AI 怎么改

**设计原则**
- 单一职责：一个工具只做一件事
- 幂等性：多次调用结果一致，方便重试
- 副作用控制：读操作安全，写操作要谨慎

**参考实现：**
- **Qwen-Coder**：看 Agent Loop 怎么实现，工具怎么调用
- **LangChain/LangGraph**：成熟框架，学习架构设计
- **OpenAI Assistants API**：官方接口设计

**开发环境：**
- 阿里百炼：Qwen 系列&Deepseek（Qwen-Max 、Qwen-Coder）， 入职后我们有统一的平台来访问市面上的所有的大模型
- ttapi.io：访问 Claude、GPT、Gemini


---

### 3. Agent 评测

**为什么要评测？**

没有数据就不知道改进有没有用，评测是迭代的基础。

**核心指标：**

**任务完成率**
- 成功率：完全成功 / 部分成功 / 失败
- 平均步数：越少越好
- 执行时间：端到端延迟
- Token 消耗：直接关系成本

**质量指标**
- 准确性：结果对不对
- 鲁棒性：边界情况、异常输入能不能处理
- 一致性：相同输入多次运行结果是否一样

**代码生成专项：**
- 测试通过率
- 代码质量（Lint 检查、复杂度）
- 安全性（漏洞扫描）

**评测数据集：**

**综合能力**
- AgentBench：8 个环境，3000+ 任务
- GAIA：真实用户问题，多步推理

**怎么做？**
- 搭自动化评测流程
- 建任务基准库（简单/中等/困难）
- A/B 测试：对比 Prompt 版本
- 记录失败案例，分析根因

---

## 三、AI 辅助开发（必修）

### 1. AI 编码工具深度使用

**Cursor**
- Inline Suggestions：代码补全，接受或修改
- Chat 模式：解释代码、生成函数、改 Bug
- Agent 模式（Cursor）：多文件修改

**Prompt 驱动开发**
- 需求写清楚：上下文、约束、预期结果
- 迭代式对话：逐步细化，及时纠偏
- 提供相关代码：让 AI 理解你的风格

**配对编程**
- 你负责：架构设计、核心逻辑、边界情况
- AI 负责：样板代码、重复劳动、实现细节
- 实时 Review：别无脑接受 AI 的建议

---

### 2. AI 代码审查

**审查清单：**

**功能正确性**
- 满足需求吗？边界情况处理了吗？
- 错误处理完善吗？

**安全性**
- 敏感信息有没有泄露
- 依赖包安全吗

**性能**
- React 组件会不会无限重渲染
- 有没有内存泄漏（事件监听器没清理）
- 算法复杂度合理吗

**可维护性**
- 命名清晰吗？结构合理吗？
- 注释必要吗（好代码自己会说话）
- 符合项目规范吗

**AI 常见错误：**
- 用了过时的 API（训练数据老）
- 虚构函数或库（Hallucination）
- 忽略边界条件
- 错误处理不完整

**建议：**
- 建立自己的审查清单
- 记录 AI 的常见坑
- 每次都认真 Review，不要无脑合并

---

## 四、Python 入门（可选）

> 这是**学有余力**的同学的拓展内容。我们的主力语言是 TypeScript，但很多优秀的 AI Agent 项目（如 Browser-Use、LangChain）是用 Python 写的。懂点 Python 能让你更好地理解和借鉴这些项目。

### 为什么前端也值得学 Python？

- **AI 生态主力语言**：大部分 AI/ML 库、Agent 框架都是 Python 优先
- **快速验证想法**：Python 写原型比 TypeScript 快，适合快速实验
- **阅读源码必备**：想深入 Browser-Use、Skyvern 这些项目，得看懂 Python

### 快速上手路径

**对于有编程基础的你，Python 学起来很快：**

**第一步：基础语法（1-2 天）**
- 变量、函数、类（和 JS/TS 很像，语法更简洁）
- 列表、字典、集合（对应 Array、Object、Set）
- 列表推导式、生成器（Python 特色，很优雅）

```python
# Python 的简洁之美
names = [user["name"] for user in users if user["active"]]

# 对比 TypeScript
# const names = users.filter(u => u.active).map(u => u.name)
```

**第二步：异步编程（重点）**
- async/await 语法（和 JS 几乎一样）
- asyncio 库的基本使用
- 异步上下文管理器（with 语句）

```python
import asyncio

async def fetch_data(url: str) -> dict:
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as response:
            return await response.json()
```

**第三步：类型标注（必学）**
- Python 3.10+ 的类型语法很像 TypeScript
- 用 mypy 做静态检查
- Pydantic 做运行时校验（类似 Zod）

```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    email: str | None = None  # 可选字段

# 自动校验，类型不对会报错
user = User(id=1, name="test")
```

### AI 场景必备库

**LLM 调用**
- `openai`：OpenAI 官方 SDK
- `anthropic`：Claude 官方 SDK
- `langchain`：LLM 应用框架（概念多，但值得学）

**浏览器自动化**
- `playwright`：和 JS 版 API 几乎一样
- `browser-use`：AI 驱动的浏览器自动化

**数据处理**
- `pydantic`：数据校验，AI 返回数据必用
- `httpx` / `aiohttp`：异步 HTTP 请求

### 实践建议

**从阅读开始**
1. 克隆 Browser-Use 项目
2. 跑起来，看看效果
3. 读源码，理解它怎么组织代码、怎么调用 LLM
4. 尝试改几行代码，加个小功能

**学习资源**
- [Python 官方教程](https://docs.python.org/3/tutorial/) - 快速过一遍基础
- [Real Python](https://realpython.com/) - 实用教程，质量高
- [FastAPI 文档](https://fastapi.tiangolo.com/) - 现代 Python Web 框架，学异步和类型的好材料

**环境配置**
- 推荐用 `uv`（Rust 写的包管理器，超快）
- 或者用 `poetry`（依赖管理更规范）
- VSCode + Pylance 插件，体验接近 TypeScript

### 注意事项

- **不要本末倒置**：Python 是加分项，TypeScript + React 才是主线
- **不用太深入**：能看懂代码、能写简单脚本就够了
- **遇到问题问 AI**：Python 语法问题 AI 解答得很好

---

## 五、资源推荐

> 🔥 必读/必用  ⭐ 推荐  💡 进阶/可选

### 官方文档
- 🔥 [React 官方文档](https://react.dev/) - **必读，先看这个**
- 🔥 [React 19 更新](https://react.dev/blog/2024/12/05/react-19) - **必读，了解最新特性**
- 🔥 [Next.js 文档](https://nextjs.org/docs) - **必读，跟着教程做**
- 🔥 [Prompt Engineering Guide](https://www.promptingguide.ai/) - **AI 方向必看**

### 开源项目（选一个深入研究）
- 🔥 [Browser-Use](https://github.com/browser-use/browser-use) - **推荐新手，Python，简单易懂**
- ⭐ [Stagehand](https://github.com/browserbase/stagehand) - TypeScript，前端友好
- ⭐ [Skyvern](https://github.com/skyvern-ai/skyvern) - 工作流编排，功能完整
- 💡 [Qwen-Coder](https://github.com/QwenLM/Qwen-Coder) - 阿里代码 Agent，源码复杂，有基础再研究

### 论文（有兴趣再看）
- ⭐ RA-Gen：arXiv:2510.08665 - 代码生成 Agent 架构
- ⭐ Beyond ReAct：arXiv:2511.10037 - 规划器中心架构
- 💡 REACT 框架：arXiv:2505.18933 - 经典 Agent 框架

### Python 学习（可选）
- ⭐ [Python 官方教程](https://docs.python.org/3/tutorial/) - 有编程基础的话几小时就能过完
- ⭐ [FastAPI 文档](https://fastapi.tiangolo.com/) - 现代 Python Web 框架，学异步的好材料
- 💡 [Real Python](https://realpython.com/) - 高质量实用教程
- 💡 [uv 包管理器](https://github.com/astral-sh/uv) - Rust 写的，比 pip 快 10-100 倍

### 工具平台
- 🔥 Cursor - **AI 编辑器，必用**
- 🔥 阿里百炼 - Qwen 系列（Qwen-Max、Qwen-Coder、Deepseek），**入职后有统一平台**
- ⭐ ttapi.io - 访问 Claude、GPT、Gemini，国内可用
- ⭐ LangSmith - 追踪调试 Agent，做评测时很有用

---

## 七、常见问题

**Q：时间不够怎么办？**
- 优先高优先级内容（React 19、Next.js、Prompt）
- 先会用，再深入
- 用 AI 加速学习, cursor 在学习上能够给你带来意外的惊喜

**Q：遇到不懂的怎么办？**
- 先问 AI（Claude 4.5 Sonnet、 Gemini 3 都不错的）
- 看官方文档
- 找好文章
- 动手实践

**Q：怎么知道学得怎么样？**
- 做项目（项目产出是最好的证明）
- 参与开源（获得反馈）
- 技术分享（能讲清楚说明懂了）

**Q：入职后还要学吗？**
- 当然！技术更新快，持续学习是必须的
- 实战场景更多，学习更有针对性

---

## 八、总结

**重点：**
- 前端：React 19 + Next.js 15/16 + 性能优化
- AI：Prompt Engineering + Agent 架构 + 评测
- 协作：AI 工具深度使用 + 代码审查

**心态：**
- 注重实践，不要只看不做
- 善用 AI，但不要盲信
- 遇到问题及时沟通
- 保持好奇心

**目标：**
- 懂原理，能指挥 AI
- 会审查，保证质量

有问题随时问，加油！

