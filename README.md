视频审核模块
========
minitrill 视频审核模块

## 模块思路
![](https://upload-images.jianshu.io/upload_images/5617720-c9b232d8baa3fcd2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 审核范围

- 用户上传的视频
- 用户的头像,上传的图片(?)

### 分析
与言论相比
1. 制作一个视频的成本更大,很少有人会因为非利益驱动而制作大量非法视频
2. 视频的传播速度快,覆盖面积大       
视频处理主要以**删除,封禁为主;锁定为辅**,尽快减少平台上的恶意视频

恶意视频性质分类
1. 色情视频
2. 低俗视频
3. 反动视频

创作类型
1. 反动视频,暴恐视频 - 多为**原创**
2. 色情视频,低俗视频 - 多为转载,截取和二次加工

### 核心思路
**将难以处理的视频,难以衡量的色情程度进行转化,转化为其他易于衡量大小的数据**       

视频 -> 图片        
图片 -> 指纹(用于相似度检索及审核去重)           
图片恶意 -> 恶意值
- 色情程度      
    * 肌肤裸露比例      
    * 人物造型　       
- 反动程度
    * 关键图像出现次数
    * 视频评论关键词

### 核心问题
1. 如何检测出恶意视频
2. 如何防止某特定主题恶意视频集中上传/过审     
3. **如何生成一个表明视频特征的指纹?**


## 功能
### 1. 色情图片识别

### 2. 图片指纹

### 3. 图片相似度
构建一个恶意视频库,通过图片指纹与相似度技术结合hash索引进行快速检索

### 4. 图片OCR

### 5. 视频言论聚合

## 策略 

### 审核策略
1. 上传的视频经过识别过审后才能播放
2. 点击量上升速度超过一定阈值的送人工审核接口

视频健康度
审核阈值

### 处理策略
* 色情视频/反动视频
  - 关键帧截图指纹加入恶意图库
  - 删除视频
  - 封禁视频上传者

* 低俗视频
  - 视频被锁定(无法新增点击量,点赞,分享且不会出现在首页及个性化推送中)
  - 视频上传者用户健康度扣20