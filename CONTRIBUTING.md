# 为 Jianwen 贡献代码

> 感谢您对 Jianwen 项目的贡献兴趣！我们很高兴与您一起工作，并感谢您帮助使这个项目变得更好！

**为了保证协作的顺畅，在合并代码前，你需要阅读以下规范：**

## 仓库职责

Jianwen 项目现有以下仓库，它们各自有不同的职责，请确保任何请求提交至合理的仓库

- **`Jianwen/`**: Jianwen 文档，包含语法规范和设计规范
- **`parser/parser/`**: Jianwen 解析器，由 Typescript 实现

## 提交语法、功能变更

在提交任何有关 `语法` 或 `功能` 变更的代码前，请先于对应仓库的 issue 中征得项目管理员或社区的同意，否则合并将不予批准。

其它类型的 PR，如“功能修复”或代码质量问题，无需征求同意，管理员会对合并进行审核。

## 快速入门

### 1. 创建功能分支

对于项目内的所有仓库，`main` 是我们的主分支，所有修改请基于 `main` 分支创建新分支。

```bash
git checkout main
git pull origin main
git checkout -b <type>/<description>
```

### 2. 进行代码更改

### 3. 自行测试所有内容

在提交 PR 之前，确保通过所有检查。

对于 `parser`：

```bash
npm test
npm run lint
npm run format:check
```

### 4. 提交您的 PR

- 以 `main` 分支为目标
- 编写清晰的描述
- 引用任何相关 issue

## 开发指南

### 分支命名规范

- **`main`**：主分支，生产就绪的代码
- **`feature/<description>`**：添加新功能
- **`fix/<description>`**：修复 bug 或已知的 issue
- **`enhancement/<description>`**：功能增强
- **`refactor/<description>`**：重构代码实现或项目架构
- **`chore/<description>`**：修改文档、配置或其它非代码操作
- **`test/<description>`**：添加或修改测试

> `<description>` 应简洁明了，使用小写字母和连字符，如 `feature/add-table-support`

### 代码标准

1. 代码职责最小化，遵循单一职责原则。
2. 文件分类正确且清晰。
3. 添加或删除依赖后，及时更新相关文档。
4. 使用英文注释代码。保持简洁，不必添加过多说明，除非改动可能引起的其它后果。
5. 谨慎进行大范围重构或技术栈变更。如有必要，在 issue 中提交建议。
6. 添加新语法前，于解析器仓库中阅读 `docs/standards.md` 以了解 AST 设计规范。

### 代码格式化

我们使用 **Prettier** 和 **ESLint** 进行代码格式化和质量检查。

#### Prettier 配置

项目使用以下 Prettier 配置（位于 `parser/parser/.prettierrc`）：

```json
{
  "singleQuote": true,
  "trailingComma": "all",
  "printWidth": 100,
  "semi": true
}
```

#### ESLint 配置

- 使用 TypeScript ESLint 进行类型感知的代码检查
- 集成 Prettier 插件，确保格式一致性
- 未使用的变量以 `_` 开头可以忽略检查

#### 推荐的编辑器设置

推荐在 VS Code 中安装以下扩展以获得最佳开发体验：

- **ESLint** (`dbaeumer.vscode-eslint`)
- **Prettier** (`esbenp.prettier-vscode`)

并在 VS Code 设置中启用保存时自动格式化：

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

### 测试规范

测试位于 `parser/parser/tests/`，使用 **Jest** 框架和**快照测试**验证 AST 稳定性：

```typescript
import { parseJianwenWithErrors } from '../../src/core/parser';

const { ast, errors } = parseJianwenWithErrors(source);
expect(errors).toHaveLength(0);
expect(ast.children).toMatchSnapshot();
```

- 新功能必须附带对应的测试用例
- 使用 `npm test -- -u` 更新快照
- 错误测试应检查 `errors` 数组中的诊断信息

---

## 提交 issue

### [bug]

- 存在问题的分支/版本
- 问题重现步骤
- 期望行为 vs 实际行为
- 错误日志或截图

### [enhancement]

- 清晰的增强描述，杜绝抽象概念
- 建议的实现逻辑

### [feature]

- 功能用途说明
- 清晰的功能描述，杜绝抽象概念
- 建议的实现逻辑

> 推荐保持与历史 issue 一致的标题格式

---

## 许可证

通过贡献，您同意您的贡献将按照与项目相同的许可证进行许可：

- 语言规范 (`Jianwen/`): [MIT](LICENSE)
- 解析器 (`parser/`): [MIT](../parser/LICENSE)

---

**感谢您为 Jianwen 做出贡献！** 🎉
