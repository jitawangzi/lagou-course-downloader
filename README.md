# lagou-course-downloader

拉勾网课程视频下载工具

# 免责声明

1. 此仓储代码仅用于学习研究，不保证其合法性、准确性、有效性，请根据情况自行判断，本人对此不承担任何保证责任。

2. 由于此仓储代码仅用于学习研究，您必须在下载后 24 小时内将所有内容从您的计算机或手机或任何存储设备中完全删除，若违反规定引起任何事件本人对此均不负责。

3. 请勿将此仓储代码用于任何商业或非法目的，若违反规定请自行对此负责。

4. 此仓储代码涉及应用与本人无关，本人对因此引起的任何隐私泄漏或其他后果不承担任何责任。

5. 本人对任何代码引发的问题概不负责，包括但不限于由代码错误引起的任何损失和损害。

6. 如果任何单位或个人认为此仓储代码可能涉嫌侵犯其权利，应及时通知并提供身份证明，所有权证明，我们将在收到认证文件确认后删除此仓储。

7. 所有直接或间接使用、查看此仓储代码的人均应该仔细阅读此声明。本人保留随时更改或补充此声明的权利。一旦您使用或复制了此仓储代码，即视为您已接受此免责声明。

# 更新日志

## 2021年6月30日

- 课程未购买时给出相应提示
- 修复配置文件课程id为空时导致的NPE问题

## 2021年6月21日

- 修复视频重复下载问题
- 修复ts临时文件删除失败问题
- 修复视频mp4下载完成后重命名失败问题
- 优化配置文件读取

## 2021年6月17日

- 修改配置读取方式，所有配置，在config.properties文件中填写
- 改进代码，防止程序中断或者假死
- 文章下载，支持精选留言
- 支持配置下载类型，可以选择：0:下载视频 1:下载文章 3：同时下载视频和文章
- 下载未完成的视频和文章，用!代替，防止视频下载不完整的情况
- 视频名称和文章名称，增加课时Id前缀，方便排序
- 部分接口增加重试功能
- 增加课时列表信息统计文件
- 下载视频，增加超时，防止下载卡死
- 增加把文章单独提取到一个文件夹的功能

## 2021年6月01日

- 阿里云私有加密视频下载解析

## 2021年5月20日

- 获取训练营课程视频和资料


## 2021年5月9日

- 获取账户下所有课程
- 加入章节历史下载记录
- 排除某些课程

## 2020年12月11日

- 解决签名不匹配问题

- 跳过未发布的课程视频

- 调整代码结构

## 2020年8月7日
- 支持最新的拉钩教育视频下载.


# 前置要求

1. **已购买**拉钩上的[视频课程](https://kaiwu.lagou.com/)

2. **成功登陆拉钩网**
   
   官网：  https://kaiwu.lagou.com/

# 其他

Lagou课程的视频现托管在阿里云，[相关文档](https://help.aliyun.com/product/29932.html?spm=a2c4g.11186623.3.1.3a082168qYWI6d)

视频元数据API接口文档:`https://help.aliyun.com/document_detail/56124.html?spm=a2c4g.11186623.2.30.14487fbfjBfxAC`

~~视频的PreAuthCode解密算法(md，后来发现是BASE64)逆向自aliplayer-min.js~~

~~视频片段使用`AES-CBC-128`加密/解密，通过分析js获取，视频的密钥在视频的m3u8文件中有地址。[相关文档](https://cloud.tencent.com/document/product/266/9638)~~

~~视频片段通过`ffmpeg`合并~~
现在直接获取视频的mp4地址，跳过了合成（当然也可以）

视频课程信息~~在视频首页html中的`<script>`标签里。~~ 现在通过`https://gate.lagou.com/v1/neirong/kaiwu/getCourseLessons?courseId={0}` 获取

程序默认下载`FHD`全高清视频源

# 如何使用

## 下载源码

打开shell或者cmd，输入`git clone https://github.com/SweetInk/lagou-course-downloader.git`

## 运行(以源码方式)

1. 下载 [IDEA](https://www.jetbrains.com/idea/download/#section=windows) ,并安装，导入之前下载好的源码

2. 成功登陆拉钩网后

3. 浏览器打开调试工具

4. 打开课程首页

    ![](http://ww1.sinaimg.cn/large/005ViNx8ly1g5mdhltkh8j31yy0mf11q.jpg)

    把上图中Cookie值，复制粘贴到`config.properties`文件中`cookie` 字段里.

    替换`config.properties`文件中的`mp4_dir`中的值为实际的值.
   
5. 运行`App#main()` 方法.

## TODO
 - [ ] 训练营课程下载重构
 - [ ] 下载判重调整
 - [X] [加入文章下载](https://github.com/SweetInk/lagou-course-downloader/issues/16)
 - [X] [阿里云点播HLS私有加密破解](https://github.com/SweetInk/lagou-course-downloader/issues/10)


