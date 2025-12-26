# DeepWhite 主题安装指南

## 快速安装

### 1. 找到 Typora 主题文件夹

#### 方法 A：通过 Typora 菜单（推荐）

1. 打开 Typora
2. 点击菜单栏：
   - **Windows/Linux**: `文件` → `偏好设置` → `外观` → `打开主题文件夹`
   - **macOS**: `Typora` → `偏好设置` → `外观` → `打开主题文件夹`

#### 方法 B：手动访问

**Windows:**
```
C:\Users\{你的用户名}\AppData\Roaming\Typora\themes\
```

**macOS:**
```
~/Library/Application Support/abnerworks.Typora/themes/
```
或者在终端运行：
```bash
open ~/Library/Application\ Support/abnerworks.Typora/themes/
```

**Linux:**
```
~/.config/Typora/themes/
```

### 2. 复制主题文件

将 `deepwhite.css` 文件复制到主题文件夹中。

### 3. 重启 Typora

完全关闭 Typora 后重新打开。

### 4. 选择主题

在 Typora 菜单栏中：
- 点击 `主题` → `Deepwhite`

## 验证安装

打开 `preview.md` 文件，查看各种样式是否正确显示。

## 常见问题

### Q: 主题没有出现在菜单中？

**A:** 请检查：
1. 文件名是否正确：`deepwhite.css`（全小写）
2. 文件是否放在正确的 themes 文件夹中
3. 是否完全重启了 Typora（不是最小化）

### Q: 字体显示不正常？

**A:** DeepWhite 主题使用系统默认字体：
- **macOS**: SF Pro Text / PingFang SC
- **Windows**: Segoe UI / Microsoft YaHei
- **Linux**: Ubuntu / Noto Sans SC

如果字体显示异常，可能是系统缺少相应字体。主题会自动回退到系统可用字体。

### Q: 如何自定义主题？

**A:** 编辑 `deepwhite.css` 文件，修改开头的 CSS 变量：

```css
:root {
  /* 修改背景色 */
  --bg-color: #ffffff;
  
  /* 修改文字颜色 */
  --text-color: #333333;
  
  /* 修改版心宽度 */
  --content-max-width: 860px;
  
  /* 更多变量... */
}
```

修改后保存文件，在 Typora 中切换到其他主题再切换回来即可看到效果。

### Q: 导出 PDF 时样式不对？

**A:** DeepWhite 主题已针对 PDF 导出优化。如果仍有问题：
1. 确保使用最新版本的 Typora
2. 在导出设置中选择"使用当前主题"
3. 检查是否启用了"打印背景图形"选项

### Q: 代码高亮颜色可以修改吗？

**A:** 可以。在 `deepwhite.css` 中搜索 `.token` 相关样式，修改对应的颜色值：

```css
.token.keyword {
  color: #2876d9; /* 修改关键字颜色 */
}

.token.string {
  color: #4caf8c; /* 修改字符串颜色 */
}
```

## 卸载主题

1. 打开 Typora 主题文件夹
2. 删除 `deepwhite.css` 文件
3. 重启 Typora

## 更新主题

1. 下载最新版本的 `deepwhite.css`
2. 覆盖主题文件夹中的旧文件
3. 重启 Typora

## 技术支持

如果遇到其他问题，请检查：
- Typora 版本是否为 1.0.0 或更高
- 操作系统是否支持
- 是否有其他主题或插件冲突

---

**祝你使用愉快！** 📝
