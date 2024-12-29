---
title: node实现鼠标点击事件
date: 2024-11-11T21:04:07+08:00
tags: []
series: []
featured: false
---
碰到一个网站，页面刷新浏览量自动加2，试一下看能否自动点击鼠标实现浏览量增加！

<!--more-->

#### **一、实现鼠标点击动作：**

1、node init初始化一个项目

2、新建文件index.js

3、复制下面代码进index.js文件，后运行node index.js

实现鼠标自动点击：

```javascript
const { mouse } = require('@nut-tree/nut-js');

(async () => {
  try {
    // 设置屏幕分辨率（根据你的屏幕调整）
    const screenWidth = 2560;  // 假设你的屏幕宽度是2560
    const screenHeight = 1440; // 假设你的屏幕高度是1440

    // 移动鼠标到屏幕中心
    await mouse.move({ x: screenWidth / 2, y: screenHeight / 2 });

    // 循环点击100次
    for (let i = 0; i < 50; i++) {
      await mouse.leftClick();  // 执行右键点击
    //   console.log(`Click #${i + 1}`);
    }

    console.log('Completed 100 right-clicks!');
  } catch (error) {
    console.error('Error occurred:', error);  // 捕获并打印错误信息
  }
})();

```

**关于nut.js**： 

`nut.js` 是一个用于自动化鼠标和键盘控制的 Node.js 库，它通过模拟鼠标移动、点击、键盘输入等操作来进行自动化任务。这个库特别适合做 GUI 自动化测试、自动化操作、脚本化的用户交互等任务。`nut.js` 可以被广泛应用于自动化测试、自动化桌面任务等场景。

---

#### 二、点击太慢了，以下为并行访问

第一思路：只发送GET请求，来增加访问量！发现get请求数据成功但访问量不会增加，模拟请求头也不行，遂改为直接打开浏览器访问！（node还有个库专门识别图像进行自动化点击，这个库识别图片失败，就没再深入！）

```javascript
const puppeteer = require('puppeteer');

// 请求的目标URL
const url = 'https://xxx.xxx';

// 最大并行浏览器数
const maxConcurrency = 20;
// 每个浏览器运行的请求次数
const totalRequests = 200;
// 每个请求之间的延迟（200毫秒）
const delay = 200;

const sleep = (ms) => new Promise(resolve => setTimeout(resolve, ms));

const fetchWithPuppeteer = async () => {
  // 创建一个存储任务的队列
  const tasks = [];
  
  // 创建任务函数
  const task = async (browserIndex) => {
    const browser = await puppeteer.launch({ headless: true });
    const page = await browser.newPage();
    let retries = 0;
    
    for (let i = 0; i < totalRequests; i++) {
      let success = false;
      while (retries < 3 && !success) { // 最大重试次数为3次
        try {
          await sleep(delay); // 每个请求间隔200ms
          await page.goto(url, { waitUntil: 'load' });
        //   console.log(`Browser ${browserIndex}: Request ${i + 1} - Page Loaded`);

          // 模拟滚动页面
          await page.evaluate(() => window.scrollBy(0, window.innerHeight));

          success = true; // 标记成功
        } catch (error) {
          retries++;
          console.error(`Browser ${browserIndex}: Request ${i + 1} failed - Retry ${retries}/3`, error);
          if (retries >= 3) {
            console.error(`Browser ${browserIndex}: Request ${i + 1} failed after 3 retries.`);
          }
        }
      }
    }

    await browser.close(); // 完成任务后关闭浏览器
    console.log(`Browser ${browserIndex}: All requests completed.`);
  };

  // 启动最多5个浏览器实例并行处理200次请求
  for (let i = 0; i < maxConcurrency; i++) {
    tasks.push(task(i + 1)); // 将任务推入任务队列
  }

  // 等待所有任务完成
  await Promise.all(tasks);
  console.log('All requests have been completed.');
};

fetchWithPuppeteer().catch((err) => console.error('Error in fetchWithPuppeteer:', err));

```

（经测试同时开20个浏览器运行最佳）每秒能增加一百多的访问量



引用库介绍：**Puppeteer** 是一个由 **Google Chrome 团队**开发的 Node.js 库，用于控制 **Headless Chrome**（无头浏览器）或者全功能的 Chrome 浏览器。它为开发者提供了一个高级 API，用于自动化浏览器任务，如网页爬取、界面测试、截图、生成 PDF 等。Puppeteer 是一个非常强大的工具，尤其适用于需要与网页交互、执行 JavaScript 或模拟用户行为的场景。



