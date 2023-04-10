# WeiboDatasets

<p align="center">
  <a href="https://github.com/liurundong2021/WeiboDatasets/blob/master/LICENSE">
        <img src="https://img.shields.io/github/license/liurundong2021/WeiboDatasets.svg"
             alt="GitHub license">
  </a>
</p>

本项目为面向[微博](https://weibo.com)平台的，以**关键词**检索结果为主要内容构建的数据集，通过自编爬虫获取。

## 项目特点
 - 数据都是原创内容，数据质量高
 - 有一定的时间跨度，基本含盖一个舆论事件的生命周期
 - 案例丰富多样，有代表性，具有研究价值
 - 适合用作舆情、NLP 等相关领域的研究
 - 持续更新和完善

## 数据采集逻辑
![](./.github/advance_search.png)
微博平台提供的高级检索功能能让用户对**关键词**、**类型**、**包含**、**时间区间**进行配置，以实现更为精准的检索。

### 时间区间
高级检索规则限定的最小单元为 1 小时，从开始时间到结束时间按小时遍历进行检索爬取。

### 检索结果
微博检索最多展示 50 页检索结果，每页 10 条记录，按发布时间由后往前排列。同时由于最小时间单元为 1 小时，也即同一检索规则下，单小时时间区间内最多获取 500 条博文数据，即使当小时内有超过 500 条的博文数据。为了尽可能对数据进行全量收集，在采集过程中遍历高级检索中所有的类型和包含条件，对结果进行去重后整理发布。

<img src="./.github/page_list.png" width="50%" />

## 数据格式
单个文件采用 ```jsonl``` 的格式进行存储，一行为一个 ```json``` 字符串，记录了一条博文的相关数据。

数据样例：
```json
{
    "_id": "4884054899426879",
    "mblogid": "MzgEpDymr",
    "created_at": "2023-03-28 00:01:32",
    "geo": null,
    "ip_location": "发布于 江西",
    "reposts_count": 0,
    "comments_count": 0,
    "attitudes_count": 1,
    "source": "<a target=\"_blank\" target=\"_blank\" target=\"_blank\" target=\"_blank\" href=\"https://app.weibo.com/t/feed/PBfri\" rel=\"nofollow\">OPPO A58 5G</a>",
    "content": "存个 445521[亲亲][亲亲]你不知道张继科是445天最快大满贯吗？ ",
    "pic_num": 1,
    "isLongText": false,
    "user": {
        "_id": "5683039178",
        "avatar_hd": "https://tvax2.sinaimg.cn/crop.0.0.1080.1080.1024/006cBs6ely8hch5zxkhxqj30u00u0n0j.jpg?KID=imgbed,tva&Expires=1680929353&ssig=43avaY67En",
        "nick_name": "万有引力定律·",
        "verified": false,
        "mbrank": 1,
        "mbtype": 2
    },
    "pic_urls": ["https://wx1.sinaimg.cn/orj960/006cBs6egy1hcev23hj34j30k00ed76a"],
    "url": "https://weibo.com/5683039178/MzgEpDymr",
    "keyword": "张继科",
    "crawl_ts": 1680918553
}
```
### 文件命名
```<爬取方法>_<关键词>_<类型>_<包含>_<开始时间>_<结束时间>_<数据条数>```

## 数据说明
 - 张继科：2023 年 3 月底曝光的张继科涉赌涉传播他人隐私视频事件。
 - 孙国友：2023 年 3 月底的宁夏孙国友跪地求水事件。
 - 中国电科：2023 年 4 月初引发舆论风波的员工怒怼领导谣言事件。

## 授之以渔
本数据集通过[这个](https://github.com/liurundong2021/WeiboSpider)爬虫程序进行收集。

## 声明
1. 本数据集免费开源，仅供科研学术交流使用，禁止商用，如有法律风险需自行承担。
2. 使用需注明出处。