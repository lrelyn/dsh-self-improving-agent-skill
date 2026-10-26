# AGENT_MEMORY

> 这是 `AGENT_MEMORY.md` 的样例，演示协议期望的记录形态。
> 实际使用时，复制本文件为项目根目录的 `AGENT_MEMORY.md`（或 `~/.agent-memory/AGENT_MEMORY.md` 做全局），然后按同样格式持续追加。
> 新条目放最上面。

## 用法约定

- 任务开始前：扫一眼本文件，找与本任务相关的历史教训。
- 任务结束后：追加一条，哪怕只有一句话。
- 能客观判定成败的（退出码、文件是否存在、测试是否通过、HTTP 状态码），一律用客观标准。
- 每个作用域只维护一份，不要散落副本。

---

### 2026-10-26 用 pnpm 安装桌面 profile 插件

- 成功点：三个插件都先从 npm 下载 tarball、校验 SHA1 一致后，固化成 `file:` 本地依赖放进 `vendor/`，再装——避免将来上游下架导致整体 install 失败。
- 失败点/坑：某个包在 npm 上已 404，但之前手动装进过 node_modules，导致每次 `pnpm install` 都在解析阶段报错中断。解法是把已装目录打成 tarball 固化。
- 下次改进：新插件一步到位——先下载 tarball + 校验 + 写 `file:` 依赖 + 加进 bundles，不要先临时 npm 装再补。
- 可复用经验：
  - 校验：`Get-FileHash xxx.tgz -Algorithm SHA1`，与 npm registry 的 `dist.shasum` 对比
  - 依赖形态：`"pkg": "file:./vendor/pkg-x.y.z.tgz"`

### 2026-10-25 排查"安装成功但界面没生效"

- 成功点：最后用进程命令行（`Get-CimInstance Win32_Process`）确认了插件确实被主进程加载，而不是只看 package.json 里写了。
- 失败点/坑：一开始把"文件存在"当成"已生效"，其实还需要重启宿主。
- 下次改进：判断"生效"必须有三层证据——依赖已装、宿主进程已加载、界面/功能实际可用。
- 可复用经验：查进程命令行比查文件更能证明"真的在跑"。
