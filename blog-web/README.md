<!--
 * @Author: fangyalong 1921934563@qq.com
 * @Date: 2023-10-28 10:21:28
 * @LastEditors: fangyalong 1921934563@qq.com
 * @LastEditTime: 2023-11-01 15:56:49
 * @FilePath: \blog-web\README.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
## 开发

```bash
# 克隆项目
git clonhttps://github.com/fangyalong/blog2.git

# 进入项目目录
cd BLOG-WEB

# 安装依赖
npm install

# 建议不要直接使用 cnpm 安装依赖，会有各种诡异的 bug。可以通过如下操作解决 npm 下载速度慢的问题
npm install --registry=https://registry.npmmirror.com

# 启动服务
npm run dev
```

浏览器访问 http://localhost:80

## 发布

```bash
# 构建测试环境
npm run build:stage

# 构建生产环境
npm run build:prod
```


### 添加功能的
feat: 

### 修改bug的
fix:

### 重构代码
refactor：