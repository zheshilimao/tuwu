# 🌹 土味情话生成器

这是一个基于随机台词 API 的 **土味情话网页展示项目**，通过美观的卡片风格把原始数据转换成易读、可复制、好看的情话体验页。

👉 在线演示地址:  
**https://zheshilimao.github.io/tuwu/**

---

## 🧠 背后来源

本项目的数据来源于：

🔗 **API 接口（随机情话生成）**  
👉 https://new-qk.lifves.com/index.php

该接口返回随机情话内容（常带对话格式），我们通过前端代码对 API 返回的数据进行处理和展示。

---

## 💡 项目功能

- 🌟 **对话式展示风格**  
  自动将返回内容按台词格式拆分并一条条显示

- 🖼️ **简洁卡片界面设计**  
  居中大字体 + 圆角卡片 + 轻柔背景，阅读体验舒服

- 🔄 **点击屏幕换一句**  
  点击页面即可抓取并显示下一条情话

- 📋 **右下角轻量复制按钮**  
  点击复制当前情话内容，方便分享

---

## 🔧 实现原理

1. 页面通过 JavaScript 调用：

https://new-qk.lifves.com/index.php

2. 获取返回的文本（带台词格式）

3. 通过 JS 处理：
- 去掉最外层双引号（如果有）
- 把 `\n` 转为换行
- 按行拆分展示

4. 将处理后的文本填充到页面中

---

## 📦 代码展示（核心逻辑）

```javascript
fetch("https://new-qk.lifves.com/index.php")
.then(res => res.text())
.then(data => {
 // 去掉最外层双引号
 data = data.replace(/^"+|"+$/g, "");

 // 处理 \n 换行
 data = data.replace(/\\n/g, "\n");

 // 拆分为多行台词
 let lines = data.split("\n");
 let html = "";
 for (let line of lines) {
     if (line.trim() !== "") {
         html += "<div class='line'>" + line + "</div>";
     }
 }
 document.getElementById("text").innerHTML = html;
});


---

🧪 如何使用

1. 打开页面
👉 https://你的用户名.github.io/love/


2. 点击页面任意位置
👉 切换下一句台词


3. 点击右下角“复制”按钮
👉 复制当前内容到剪贴板




---

🎨 项目结构

📦love
 ┣ 📄index.html         # 网页核心展示文件
 ┣ 📄README.md          # 项目说明文档
 ┗ 📄其他资源文件       # 可选 CSS/图片等


---

📢 许可 & 免责声明

本项目仅用于学习和展示，不用于商业用途。
API 来源于第三方公开数据接口，如使用请遵循 API 原站的使用条款。


---

❤️ 致谢

感谢提供情话数据的接口服务： 👉 https://new-qk.lifves.com
