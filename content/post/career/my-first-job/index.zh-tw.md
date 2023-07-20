---
title: 从第一份工作辞职的记录
description: 副标题是当一个公司有一个cultist head of engineering和一个喜欢micro-manage的CEO时会碰撞出什么样的火花
date: 2023-05-26
image: building.jpg
slug: why-i-quit-my-first-job
tags:
    - tech
    - job
    - e-commerce
    - data engineering
    - search
categories: 
    - career
toc: true
lang: zh-tw
readingTime: true
---

> Disclaimer: The names, organizations, and events mentioned in this article are purely fictional. Any resemblance to actual names, organizations, or events is purely coincidental. The purpose of this article is to create a fictional context for illustrative or entertainment purposes. The author and the publisher do not intend to offend or infringe upon the rights of any real names, organizations, or events.

## 裁员潮

从23年四月底跟direct manager提出离职到现在已经有一个月了，也希望能记录一下这段时间的心路历程，以此祭奠毕业以来的第一份工作。

虽然四月才正式辞职，但是想要走的想法在去年九月第一波大规模裁员的时候就已经萌发。21年和22年前半年管理层在世界地图上像扔飞镖一样开拓市场，欧洲的法国波兰西班牙，南美洲的阿根廷。然而这些市场无一不在开放几个月草草收场，伴随着的是拿不回来的已经被marketing和promotion烧掉的真金白银和花大价钱招来的尾大不掉的R&D部门。现金流出现危机之后，公司终于在22年九月宣布将要大裁员。要裁员的流言早就在员工中流传，直到裁员前一天的晚上HRBP给所有人book了第二天早晨的一个十五分钟的townhall尘埃落定。公司管理层在所谓的townhall上出现了不到五分钟宣布“我们sadly要对人员做一些调整，我们会妥善补偿受到影响的员工，farewell and goodbye”。现在看来我司在裁员这方面走在了业界的第一线。

我所在的data engineering组没有受到大的影响，但是还是在上午还在对接的同事下午就消失不见的惴惴不安的气氛中煎熬。大组有大概10%的员工被lay off，同组留下来的人在之后逐渐地选择了离开，不到两年工作经验的我成了数据工程组里最senior的人之一。

大裁员后，公司冻结了年度涨薪，大规模地削减年终奖，pantry冰箱里之前种类丰富的饮料现在只剩下了牛奶和豆奶（美其名曰帮助员工增加resilience）。零食货架一度消失，后来即使虽然又出现了，但是货架上已经没有大于1SGD的零食。因为不再购买nespresso的胶囊，租借的咖啡机也顺理成章地退还了回去，每天员工能喝到的是由公司的清洁人员（是一个非常勤劳负责任的auntie）加到现磨咖啡机里的不知品牌产地的咖啡豆，引用某位咖啡爱好者的原话是“没有香味，只有苦味”。团建的经费被全部停掉，办公室gym的instructor也连同他的办公桌被裁掉（也有silver lining，就是可以随时随地去gym不用再预约），公司减少了清洁开支导致卫生间和单人小隔间里有异味，甚至连卫生间的纸巾也从双面被替换为了单面。总而言之这家公司用上了一切可能将现金流归正的方法。

在今年3月的时候，公司又对中国区的员工提供了一个独家福利，可以自愿选择拿三个月的severance被裁。

## 我的职业生涯

大学期间和同届比起来我只有一段学校要求的internship的经历，好巧不巧地赶上了COVID pandemic，intern的公司顺势也冷冻了headcount，直到20年下半年才开始陆陆续续地开始投简历。最终一共可能投了不到十份简历，收穫两个面试和一个最终的offer，就没怎么多做选择地接受了。一年之后正式入职被大老板分配到了搜索业务的数据组，在电商领域属于比较核心的业务。

一开始加入组内的时候，搜索的数据组所使用的infra还是独立于公司infra团队的，spark airflow dolphinscheduler这些工具也有专门的负责团队部署（我离职的时候，在我之前入职的老员工已经全部离开了公司）。

期间参与了三个data warehouse项目的主要设计和开发，经历了两次reorg换direct manager。现在马上要走了回想起来还是有点唏嘘，自己倾注了心血的项目之后不知道会被扫到哪个垃圾堆里。

## Decision to Leave

1. 极其匮乏原始而不稳定的Data Infrastructure & Internal Tools

管理层达成了“我们的数据体量过于庞大所以不能用公有云因为太贵了，我们要招数据基建团队然后开发自己的内部云平台”的统一意见，于是我们21年底开始大规模交出团队下属的机器给数据基建团队统一规划，然后从自己随手搭的YARN airflow等等工具迁移到基建团队开发的内部云平台。然而内部云平台的各种组建实在是过于原始和不稳定，这直接导致了我们每天的工作产生了巨大的friction。

- Data pipeline所依赖的几个组件，spark hive yarn, 经常因为机房只要其中一个处于不可用状态那么我们的任务就会大规模失败，需要依赖人力去修复几十上百个相互依赖的任务。这种事情两年的时间内发生了不下几十次，每发生一次就会导致我们一整天不用干其它事情了。
- 所有的组件只能保证在chrome上可用，在2023年也属于非常离谱的事情。
- 内部的调度平台，及其难用而且充满各种无意义的user friction，根本想象不到这样的产品如果上到市场上能有任何的竞争力（但这估计也是各种内部组件的通病，因为团队的performance由老板决定而不由真正的用户决定，而且内部的数据产品并没有任何ToB的计划，所以自然而然的老板的需求priority远高于用户需求的priority，甚至还会抵触接受用户的feedback因为徒增工作量而不增加老板眼里的impact）。
  - 在Rerun/Backfill界面无法看到任务的名字，只有当前行为无意义的代号。如果你想找到每个operation对应具体哪个任务需要经过一个长到离谱的点击序列
  - 使用过程中各种无意义徒增腱鞘劳损的friction，比如无法右键给DAG里的任务新开一个tab，只能点击跳转->复制URL到新tab->返回DAG，显示过往任务执行情况的matrix view不能多选只能一个一个处理。
  - 非常丑陋的界面设计和字体选择，每天看到眼瞎。
- Code Editor产品，长期无法修复滚轮会randomly跳转到光标的恶性bug。无法批量修改任务导致每次更改config都要手动一个一个地修改。没有integrate git而是自己开发了一个version control系统（Update：新司居然也是使用这样一套系统），无法atomically更改changes而是需要手动create version snapshot，而且回滚只能回滚到某一个版本的完全状态。
- 团队从PM lead到产品dev每个人都仿佛我们欠了他们八百万，scold用户是家常便饭。对于用户提出的feedback也是能推掉就推掉，以教育用户为主。但这可能也是所有内部工具团队的普遍状况，因为开发的产品并不是以市场为导向而是以老板为导向，用户的需求即使做了，在老板眼里也没有相应的impact。
- 从22年底到现在，新加坡没有预算开设新的机房，我们必须用有限的计算资源应对每天都会到来的数据需求，而且因为data pipeline任务没有支持global config的功能，经常有不熟悉数据开发的dev申请巨量的资源用光计算队列，每天的有相当多的时间浪费在发现这些illy-configured的任务，和删除cold data剩下空间之中。而且因为内部没有一个可用的数据治理的工具，发现某个project下schema中哪些表的数据量或者文件数量最大需要手动跑很多command。
  
2. 没有长期规划，项目随着组织结构的调整启用和废弃

公司的数据组织架构是业务下属的烟囱型数据团队和公司共用的数据平台团队并行，在较核心和复杂的业务使用前者而公司可以共用的数据使用后者。而属于业务的数据团队要同时负责BI/PM的数据分析需求和machine learning/algorithm团队模型训练的需求。

在我加入团队后先是为算法团队开发了一版数仓，后来这一版数仓随着对方团队的组织结构调整而大范围的弃用（除了少数表之外）。

之后我们参与了从Data Mart团队接收搜索相关的数仓的project，对方团队参与公司早期搜索业务数据的开发（使用scala和spark2），而公司后来的方向是数据团队下属于业务团队。我们的首要任务是从数据团队搭建的airflow上调度的复杂pipeline迁移到公司内部的调动平台（使用到了我自己写的一个小migration script），然后保证任务的稳定运营。

同时我们和当时的搜索PM lead kick-off了重构新数仓的project（使用内部平台和sparkSQL），并且最终的目的是在替换老数仓的前提下保证更好的SLA和数据质量，然而这些目标随着对方PM lead的离职和搜索业务的组织架构调整全部没有完成。

大约今年二月的时候公司宣布要把主要base在Beijing的video团队和搜索推荐团队合并，我也换了一个lead，之前接手的项目可以说是大半白做，因为新lead打算做一个unified data warehouse而不是继续维护开发旧的版本，这里我也不想对不同地区Office之间的politics做过多的展开。

3. 和底层完全脱节，没有人文关怀的管理层

Quickmart的管理层做出的决定往往令人血压升高，这也是我决定离开这家公司的重要原因之一。
- 堪比新闻联播的townhall
  一开始（2021年）的产研townhall上live Q&A是启用的，而且不会有提前对于问题的审查。经常可以看到一些尖锐的问题，比如PM序列的待遇为什么比dev低那么多而且晋升难度大，今年的涨薪是否可以达到往年的预期，为什么只要学历光鲜即使没有行业的经验也可以开到比老员工更多的薪水等等。管理层即使不能很好的直面每一个问题，但至少大家所关心的内容都会暴露出来。

  再后来，townhall逐渐演变成了一个固定的模板 - 一开始挑选几个做得好的团队做成果展现，强调一下我们的value (serve the underserved)，展望一下未来，然后Q&A环节分为两块 - pre-selected questions 和所谓的live questions，live questions不能现场提出而是要通过HR预先准备好的portal来投递并且审查，过于尖锐的问题肯定是不会被选出的，所以最后呈现的结果就是些不痛不痒的问题，比如公司管理层觉得员工应该如何学习公司的降本增效方针，管理层觉得在目前动荡的市场条件下公司如何继续保持竞争力等等。

  不过这样也闹了很多笑话，比如CEO在连续三次townhall上被问到今年年终怎么办的时候回答"We're still discussing it"。
  
  我仍清晰地记得在被问到为什么如此苛刻地削减员工福利，甚至是开销并不大的饮料和零食时，某位chief车轱辘话了用了好几种方式表达“我们要培养cost-concious意识”。

  此后还有一系列匪夷所思的政策，比如施行了两个星期的hot-desking，和迅速安装在门禁上的签到系统，实在是冠绝一筹科技公司们。

  没有人文关怀指的是去年九月的裁员过于暴力迅速，大意就是拿了钱快滚，之后的保险政策和相关的失业时期的辅助policy是根本没有，从此之后公司的IM就只能保留半年的消息记录了我也不知道是不是和怕员工翻旧账有关，不过就职期间确实发生过很多次员工因为不满公司政策在大群怼管理层的情况。

4. 工作日趋琐碎

因为缺乏成熟的CICD工具和批量处理的方法，团队内部也没有多余的人力来开发，导致无论是对于任务config的调整，每天的SLA保证，还是数据质量的监测都变得非常tedious，后来每次遇到相关的问题都很抑郁，因为又需要put in a lot of human efforts。

5. 员工没有morale

做得好或者差都一样没有年终奖升值加薪，那自然每个需求都是能拖则拖咯。

## 重新求职

一开始想着先刷刷题准备准备于是只回复了Linkedin上主动reach out的猎头（和猎头聊天真的很boost confidence），之后约到了五次面试机会，其中三个给了offer。今年七月的时候入职了新工作。

## 结语

对QuickMart的感情很复杂，在这份工作里确实学到了不少的东西。遇到了非常善良可爱的同事们，大家经常一起摸鱼聊各种有的没的，也很感谢给过我帮助的lead和组员们。现在是时候说再见啦。

这大概就是我第一份工作的记录。