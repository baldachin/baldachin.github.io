# Pagefind 搜索设置指南

## 概述

本项目已配置为使用 Pagefind 进行客户端搜索，替代了原来的 fuse.js。

## 已创建/修改的文件

1. `layouts/_default/search.html` - 自定义搜索页面布局
2. `assets/js/pagefind-search.js` - Pagefind 搜索脚本（回车键触发搜索）
3. `hugo.yaml` - 已注释 fuse.js 配置
4. `.gitignore` - 添加了 Pagefind 索引目录

## 使用方法

### 1. 构建网站

```bash
cd hugo/MyFreshWebsite
hugo
```

### 2. 生成 Pagefind 索引

```bash
npx pagefind --source public
```

或者使用 npm 脚本（如需在 package.json 中添加）：

```json
{
  "scripts": {
    "build": "hugo && npx pagefind --source public"
  }
}
```

### 3. 本地测试

```bash
# 启动本地服务器预览
cd public
python -m http.server 8080
# 或使用其他 HTTP 服务器
```

访问 http://localhost:8080/search/ 测试搜索功能。

## 搜索功能说明

- **触发方式**：输入关键词后按 **回车键** 开始搜索
- **中文支持**：由于使用回车键触发，中文输入法不会有卡顿问题
- **键盘快捷键**：
  - `ESC`：清空搜索
  - `↑` / `↓`：在结果中导航
  - `→` / `Enter`（选中结果时）：打开链接
- **高亮显示**：Pagefind 会自动高亮搜索关键词

## 回滚方案

如需恢复到 fuse.js：

1. 删除 `layouts/_default/search.html`
2. 删除 `assets/js/pagefind-search.js`
3. 取消 `hugo.yaml` 中 `fuseOpts` 的注释
4. 重新运行 `hugo`

## GitHub Actions 集成

如需在 CI/CD 中自动生成索引，可在 `.github/workflows/hugo.yml` 中添加：

```yaml
- name: Build with Hugo
  run: hugo --minify

- name: Build Pagefind search index
  run: npx pagefind --source public
```
