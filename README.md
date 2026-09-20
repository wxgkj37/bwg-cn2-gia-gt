# 搬瓦工 CN2 GIA vs CN2 GT：一条线路看懂回程差异，附套餐价格与机房选择建议

在搬瓦工（BandwagonHost）的购买页面里，CN2 相关套餐占了很大比重。但很多人下单前真正纠结的问题其实是：CN2 GIA 和 CN2 GT 到底差在哪？多花的钱值不值？GT 现在还能不能买？这篇文章把这两条线路的技术差异讲清楚，再对照搬瓦工当前在售的全系套餐，给出按预算和用途选择的具体建议。

## CN2 是什么，GIA 和 GT 差在哪

CN2 是中国电信的下一代骨干网，走这条网络的 ASN 是 AS4809。搬瓦工官方的技术页面对电信的几种跨境通道做过明确区分：AS4134（163 骨干网）、CN2 GT、CN2 GIA 和 CTGNet（AS23764），等级依次拉开。

**CN2 GT（Global Transit）** 是电信的中端线路。它出现的初衷是解决 163 骨干网的拥塞问题，资费也确实更贵。但根据搬瓦工官方页面的说法，2019 年之后 CN2 GT 的表现和 163 骨干网已经相差不大，也就是晚高峰照样会拥堵——尽管它的成本比 163 高出不少。

**CN2 GIA（Global Internet Access）** 是电信最高等级的商用线路。它的特点是双向全程走 CN2 网络，官方对它的评价是"多年来观察到的问题最少、非常稳定"。代价同样直白：CN2 GIA 的 IP 专线成本最高可达每兆比特 120 美元，1Gbps 带宽在某些市场的月账单能到 10 万美元级别。这也是为什么 GIA 套餐的价格始终降不下来。

一个中文技术社区的判断方式更直观：看回程路由，全程都走 59.43 开头节点的是 GIA；出了国际出口就切回 202.97（163 骨干网）的是 GT。自己用 traceroute 测一次就知道手里的机器是哪种。

另外补充一点：联通和移动用户感知差异会小一些，因为 GIA 套餐通常同时叠加了联通 9929（AS10099）和移动 CMIN2（AS58807）的优化回程，三网都能受益。

## 两者在搬瓦工套餐里的具体体现

理解了线路等级，再看搬瓦工的产品线就清晰了。目前官网在售的套餐大致分四档，对应线路如下：

| 套餐系列 | 线路定位 | 带宽 | 可选机房 |
| --- | --- | --- | --- |
| KVM PROMO（20G-480G） | 普通国际线路（原 CN2 GT 机房已调整） | 1Gbps | 洛杉矶 DC2/DC4/DC8 等 9 个 |
| DC9 CN2 GIA | 电信 CN2 GIA，三网直连 | 1Gbps | DC9 专用 + 普通 KVM 机房 |
| CN2 GIA-E（DC6 ECOMMERCE） | CN2 GIA 电商优化版，三网回程 GIA | 2.5Gbps 起 | 14 个，含 DC6/DC9/日本软银 JPOS_1/荷兰 EUNL_9 |
| 香港/东京 CN2 GIA | 大陆方向直连，延迟最低 | 1-1.2Gbps | 固定机房，不可迁移 |

这里有个变化值得说明：搬瓦工早期的 CN2 GT 是通过 DC3、DC8 这些机房提供的，也是老用户口中"CN2 套餐"的来源。随着产品线调整，CN2 GT 已经逐步退场，现在的 KVM 常规套餐（DC2 AO、DC8 ZNET、DC4 MCOM 等）更接近普通国际线路。如果你看到标注"CN2"或"CN2 GT"的旧文章，价格和机房大概率已经过时，下单前要对一下当前页面。

2021 年前后 GT 阵营还有过 HIBW1/HIBW2 这类月流量 12-16TB 的大流量套餐（$99.99-$129.99/月），如今也只存在于历史记录里了。

## 当前在售套餐全表与价格

下面是官网购物车当前公开的所有套餐系列。搬瓦工不支持月付是常态（最低计费周期为季度或半年），只有迪拜等少数套餐例外。

| 套餐 | 核心配置 | 价格（USD） | 计费周期 | 购买链接 |
| --- | --- | --- | --- | --- |
| KVM PROMO 20G | 1核/1GB/20GB SSD/1TB流量/1Gbps | $49.99 | 年付 | [ 查看 KVM 20G 套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=44) |
| KVM PROMO 40G | 2核/2GB/40GB SSD/2TB流量/1Gbps | $52.99 半年付；$99.99 年付 | 半年/年付 | [ 查看 KVM 40G 套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=45) |
| KVM PROMO 80G | 2核/4GB/80GB SSD/3TB流量/1Gbps | $19.99 月付；$59.99 季付；$199.99 年付 | 月/季/半年/年付 | [ 查看 KVM 80G 套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=46) |
| KVM PROMO 160G | 2核/8GB/160GB SSD/4TB流量/1Gbps | $39.99 月付；$399.99 年付 | 月/季/半年/年付 | [ 查看 KVM 160G 套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=47) |
| KVM PROMO 320G | 3核/16GB/320GB SSD/5TB流量/1Gbps | $79.99 月付；$799.99 年付 | 月/季/半年/年付 | [ 查看 KVM 320G 套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=48) |
| KVM PROMO 480G | 4核/24GB/480GB SSD/6TB流量/1Gbps | $119.99 月付；$1199.99 年付 | 月/季/半年/年付 | [ 查看 KVM 480G 套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=49) |
| DC9 CN2 GIA 20G | 2核/1GB/20GB SSD/1TB流量/1Gbps | $31.99 季付；$113.99 年付 | 季/半年/年付 | [ 查看 DC9 CN2 GIA 20G](https://bandwagonhost.com/aff.php?aff=79616&pid=72) |
| DC9 CN2 GIA 40G | 3核/2GB/40GB SSD/2TB流量/1Gbps | $61.99 半年付；$225.99 年付 | 半年/年付 | [ 查看 DC9 CN2 GIA 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=73) |
| DC9 CN2 GIA 80G | 4核/4GB/80GB SSD/3TB流量/1Gbps | $39.99 月付；$399.99 年付 | 月/季/半年/年付 | [ 查看 DC9 CN2 GIA 80G](https://bandwagonhost.com/aff.php?aff=79616&pid=74) |
| DC9 CN2 GIA 160G | 6核/8GB/160GB SSD/5TB流量/1Gbps | $75.99 月付；$759.99 年付 | 月/季/半年/年付 | [ 查看 DC9 CN2 GIA 160G](https://bandwagonhost.com/aff.php?aff=79616&pid=75) |
| DC9 CN2 GIA 320G | 8核/16GB/320GB SSD/8TB流量/1Gbps | $143.99 月付；$1439.99 年付 | 月/季/半年/年付 | [ 查看 DC9 CN2 GIA 320G](https://bandwagonhost.com/aff.php?aff=79616&pid=76) |
| CN2 GIA-E 20G | 2核/1GB/20GB SSD/1TB流量/2.5Gbps | $49.99 季付；$169.99 年付 | 季/半年/年付 | [ 查看 CN2 GIA-E 20G](https://bandwagonhost.com/aff.php?aff=79616&pid=87) |
| CN2 GIA-E 40G（AI 部署热门） | 3核/2GB/40GB SSD/2TB流量/2.5Gbps | $89.99 半年付；$299.99 年付 | 半年/年付 | [ 查看 CN2 GIA-E 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=88) |
| CN2 GIA-E 80G | 4核/4GB/80GB SSD/3TB流量/2.5Gbps | $56.99 月付；$549.99 年付 | 月/季/半年/年付 | [ 查看 CN2 GIA-E 80G](https://bandwagonhost.com/aff.php?aff=79616&pid=89) |
| CN2 GIA-E 160G | 6核/8GB/160GB SSD/5TB流量/5Gbps | $86.99 月付；$879.99 年付 | 月/季/半年/年付 | [ 查看 CN2 GIA-E 160G](https://bandwagonhost.com/aff.php?aff=79616&pid=90) |
| CN2 GIA-E 320G | 8核/16GB/320GB SSD/8TB流量/5Gbps | $159.99 月付；$1599.99 年付 | 月/季/半年/年付 | [ 查看 CN2 GIA-E 320G](https://bandwagonhost.com/aff.php?aff=79616&pid=91) |
| CN2 GIA-E 640G | 10核/32GB/640GB SSD/10TB流量/10Gbps | $289.99 月付；$2759.99 年付 | 月/季/半年/年付 | [ 查看 CN2 GIA-E 640G](https://bandwagonhost.com/aff.php?aff=79616&pid=92) |
| CN2 GIA-E 1280G | 12核/64GB/1280GB SSD/12TB流量/10Gbps | $549.99 月付；$5399.99 年付 | 月/季/半年/年付 | [ 查看 CN2 GIA-E 1280G](https://bandwagonhost.com/aff.php?aff=79616&pid=93) |
| 香港 CN2 GIA 40G | 2核/2GB/40GB SSD/500GB流量/1Gbps | $89.99 月付；$899.99 年付 | 月/季/半年/年付 | [ 查看香港 CN2 GIA 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=95) |
| 香港 CN2 GIA 80G | 4核/4GB/80GB SSD/1TB流量/1Gbps | $155.99 月付；$1559.99 年付 | 月/季/半年/年付 | [ 查看香港 CN2 GIA 80G](https://bandwagonhost.com/aff.php?aff=79616&pid=96) |
| 东京 CN2 GIA 40G | 2核/2GB/40GB SSD/500GB流量/1.2Gbps | $89.99 月付；$899.99 年付 | 月/季/半年/年付 | [ 查看东京 CN2 GIA 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=108) |
| 东京 CN2 GIA 80G | 4核/4GB/80GB SSD/1TB流量/1.2Gbps | $155.99 月付；$1559.99 年付 | 月/季/半年/年付 | [ 查看东京 CN2 GIA 80G](https://bandwagonhost.com/aff.php?aff=79616&pid=109) |
| 大阪 CN2 GIA 40G | 2核/2GB/40GB SSD/500GB流量/1.5Gbps | $49.99 月付；$499.99 年付 | 月/季/半年/年付 | [ 查看大阪 CN2 GIA 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=134) |
| 大阪 CN2 GIA 80G | 4核/4GB/80GB SSD/1TB流量/1.5Gbps | $86.99 月付；$869.99 年付 | 月/季/半年/年付 | [ 查看大阪 CN2 GIA 80G](https://bandwagonhost.com/aff.php?aff=79616&pid=135) |
| 新加坡 CN2 GIA 40G | 2核/2GB/40GB SSD/500GB流量/1.5Gbps | $49.99 月付；$499.99 年付 | 月/季/半年/年付 | [ 查看新加坡 CN2 GIA 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=173) |
| 迪拜 ECOMMERCE 20G | 2核/1GB/20GB SSD/500GB流量/1Gbps | $19.99 月付；$169.99 年付 | 月/季/半年/年付 | [ 查看迪拜 ECOMMERCE 套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=114) |
| ECOMMERCE SLA 洛杉矶 20G | 2核/1GB ECC/20GB NVMe/1TB流量/2.5Gbps，99.99% SLA | $65.89 季付；$239.99 年付 | 季/半年/年付 | [ 查看 SLA 商务套餐](https://bandwagonhost.com/aff.php?aff=79616&pid=164) |
| ECOMMERCE SLA 洛杉矶 40G | 3核/2GB ECC/40GB NVMe/2TB流量/2.5Gbps，99.99% SLA | $116.99 季付；$399.99 年付 | 季/半年/年付 | [ 查看 SLA 商务套餐 40G](https://bandwagonhost.com/aff.php?aff=79616&pid=165) |

有两个套餐值得单独一提。CN2 GIA-E 40G 因为 2GB 内存加 2TB 流量的配置适合跑 AI 应用和代理服务，长期处于缺货状态，看到补货往往就要尽快下单。迪拜 ECOMMERCE 套餐是少有的支持月付的产品，价格和 CN2 GIA-E 一致，适合先按月试用再决定是否长期持有。

如果你不确定该选哪档，可以直接从 [👉 全部在售套餐入口](https://bit.ly/BandwagonHost) 进去看库存和机房列表。

## 怎么选：按用途对号入座

第一类，预算敏感、只跑轻量任务。学习 Linux、挂个人博客、跑脚本、做测试机，KVM PROMO 20G 的 $49.99/年足够了。它的线路是普通国际线路，电信用户晚高峰可能感觉到波动，但对这类用途影响不大。

第二类，电信用户、在意晚高峰。DC9 CN2 GIA 20G 的 $31.99/季是一个均衡选择，比 GIA-E 便宜，回程电信走 GIA。联通和移动用户从它身上获得的提升相对有限，这点要有预期。

第三类，三网用户、建站或跑生产服务。CN2 GIA-E 是目前的主流推荐。同配置下它的带宽直接翻到 2.5Gbps 起步，机房能在 DC6、DC9、日本软银 JPOS_1 和荷兰 EUNL_9 之间免费切换，回程电信 GIA、联通 9929、移动 CMIN2 全覆盖。价位从 $49.99/季的 20G 到 $169.99/季的 40G，覆盖了大多数人的预算区间。

第四类，对延迟极其敏感。香港 CN2 GIA 40G 月付 $89.99 起步，流量只有 500GB/月，但大陆方向的延迟是全场最低的。这个定位注定是小众选择，建议按月付款，用得好再考虑年付，因为香港套餐不支持迁移到其他机房。

还有一个判断方法：先看你的用户主要用什么运营商。电信用户感知 GIA 和 GT 的差异最明显；如果访问方以联通、移动为主，可以适当降低对 GIA 的执念，把预算留给更高带宽或更近的机房。

## 优惠码和下单步骤

搬瓦工的优惠码是循环折扣，续费同样生效，但力度不高，一般在 6.77% 左右。2026 年可尝试的循环码包括 **NODESEEK2026**（社区渠道流传的 6.77% 循环码）和 **BWHCGLUKKB**（历史长期码，6.78% 左右，可用性以结算页验证结果为准）。老码 BWH3YAIK50、BWHNCXNVXV 等均已过期。另外每年双十一和黑色星期五通常有力度更大的全场活动，不急的话可以等这两个节点。

下单流程本身不复杂：

1. 从上表选择套餐，点击进入购物车；
2. 选择机房位置和计费周期（注意多数套餐最低按季付）；
3. 在结算页右侧 "Promotional Code" 输入优惠码，点 "Validate Code" 验证，价格实时更新；
4. 付款方式支持支付宝，国内用户无需外币卡；
5. 开通后通过 KiwiVM 面板管理，机房之间可以免费互相迁移（香港等固定机房除外）。

结算前再确认一次库存状态。GIA 类套餐断货是常态，尤其是 CN2 GIA-E 40G 和香港系列，补货窗口可能很短。

## 常见问题

**CN2 GT 现在还能买到吗？** 基本买不到了。DC3、DC8 曾经是 CN2 GT 的主力机房，现在产品线已调整，KVM 常规套餐的机房列表里已经没有明确的 CN2 GT 定位。还在推荐"CN2 GT 套餐"的文章基本都是旧信息。

**CN2 GIA 一定比 CN2 GT 快吗？** 在中国大陆方向、尤其是电信线路上，GIA 的晚高峰稳定性和丢包控制明显更好。但如果你的使用场景和大陆方向关系不大，这个优势体现不出来，GIA 的溢价也就没必要。

**套餐买错了能退吗？** 搬瓦工有 30 天内退款政策，但仅限未使用 PayPal 争议的情况，且部分特价套餐不适用。下单前把机房和周期选对，比事后退款省事得多。

**年付和季付差多少？** 以 CN2 GIA-E 20G 为例，季付一年合计 $199.96，年付 $169.99，年付便宜约 15%。长期使用建议年付，先体验则选季付。
