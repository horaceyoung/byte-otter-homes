---
title: 从第一份工作辞职的记录
description: 副标题是当一个公司有一个cultist head of engineering和一个喜欢micro-manage的CEO时会碰撞出什么样的火花
date: 2023-05-26
image: building.jpg
slug: why-i-quit-my-first-job
tags:
    - tech
    - job
    - data engineering
categories: 
    - career
toc: false
lang: zh-tw
readingTime: true
---

> Disclaimer: The names, organizations, and events mentioned in this article are purely fictional. Any resemblance to actual names, organizations, or events is purely coincidental. The purpose of this article is to create a fictional context for illustrative or entertainment purposes. The author and the publisher do not intend to offend or infringe upon the rights of any real names, organizations, or events.

## 裁员潮

从23年四月底跟direct manager提出离职到现在已经有一个月了，也希望能记录一下这段时间的心路历程，以此祭奠毕业以来的第一份工作。

虽然四月才正式辞职，但是想要走的想法在去年九月第一波大规模裁员的时候就已经萌发。21年和22年前半年管理层在世界地图上像扔飞镖一样开拓市场，欧洲的法国波兰西班牙，南美洲的阿根廷。然而这些市场无一不在开放几个月草草收场，伴随着的是拿不回来的已经被marketing和promotion烧掉的真金白银和花大价钱招来的尾大不掉的R&D部门。现金流出现危机之后，公司终于在22年九月宣布将要大裁员（要裁员的流言早就在员工中流传，直到裁员前一天的晚上HRBP给所有人book了第二天早晨的一个十五分钟的townhall尘埃落定。公司管理层在所谓的townhall上出现了不到五分钟宣布“我们sadly要对人员做一些调整，我们会妥善补偿受到影响的员工，farewell and goodbye”）。现在看来我司在裁员这方面走在了业界的第一线。

我所在的data engineering组没有受到大的影响，但是还是在上午还在对接的同事下午就消失不见的惴惴不安的气氛中煎熬。大组有大概10%的员工被lay off，同组留下来的人在之后逐渐地选择了离开，不到两年工作经验的我成了数据工程组里最senior的人之一。

大裁员后，公司冻结了年度涨薪，大规模地削减年终奖，pantry冰箱里之前种类丰富的饮料现在只剩下了牛奶和豆奶（美其名曰帮助员工增加resilience）。零食货架一度消失，后来即使虽然又出现了，但是货架上已经没有大于1 SGD的零食。因为不再购买nespresso的胶囊，租借的咖啡机也顺理成章地退还了回去，每天员工能喝到的是由公司的清洁人员加到现磨咖啡机里的不知品牌产地的咖啡豆，引用某位咖啡爱好者的原话是“没有香味，只有苦味”。团建的经费被全部停掉，办公室gym的instructor也连同他的办公桌被裁掉（也有silver lining，就是可以随时随地去gym不用再预约），公司减少了清洁开支导致卫生间和单人小隔间里有异味，甚至连卫生间的纸巾也从双面被替换为了单面。总而言之这家公司用上了一切可能将现金流归正的方法。

## 我的职业生涯

大学期间和同届比起来我只有一段学校要求的internship的经历，好巧不巧地赶上了COVID pandemic，intern的公司顺势也冷冻了headcount，直到20年下半年才开始陆陆续续地开始投简历。最终一共可能投了不到十份简历，收穫两个面试和一个最终的offer，就没怎么多做选择地接受了。一年之正式入职被大老板分配到了数据组。期间参与了三个data warehouse项目的主要设计和开发，经历了两次reorg换direct manager。现在马上要走了回想起来还是有点唏嘘，自己倾注了心血的项目之后不知道会被扫到哪个垃圾堆里。

## Decision to Leave

1. 极其匮乏原始而不稳定的Data Infrastructure

管理层达成了“我们的数据体量过于庞大所以不能用公有云因为太贵了，我们要招数据基建团队然后开发自己的内部云平台”的统一意见，于是我们21年底开始大规模交出团队下属的机器给数据基建团队统一规划，然后从自己随手搭的YARN airflow等等工具迁移到基建团队开发的内部云平台。然而内部云平台的各种组建实在是过于原始和不稳定，这直接导致了我们每天的工作产生了巨大的friction。

- Data pipeline所依赖的几个组件，spark hive yarn, 经常因为机房只要其中一个处于不可用状态那么我们的任务就会大规模失败，需要依赖人力去修复几十上百个相互依赖的任务。这种事情两年的时间内发生了不下几十次，每发生一次就会导致我们一整天不用干其它事情了
- 所有的组件只能保证在chrome上可用，在2023年也属于非常离谱的事情。
- 仿airflow的调度平台，及其难用而且充满各种无意义的user friction，根本想象不到这样的产品如果上到市场上能有任何的竞争力（但这估计也是各种内部组件的通病，因为团队的performance由老板决定而不由真正的用户决定，所以自然而然的老板的需求priority远高于用户需求的priority，甚至还会抵触接受用户的feedback因为徒增工作量而不增加老板眼里的impact）
  - 在Rerun/Backfill界面无法看到任务的名字，只有当前行为无意义的代号。如果你想找到每个operation对应具体哪个任务需要经过一个长到离谱的点击序列
  - 使用过程中各种无意义徒增腱鞘劳损的friction，比如无法右键给DAG里的任务新开一个tab，只能点击跳转->复制URL到新tab->返回DAG，显示过往任务执行情况的matrix view不能多选只能一个一个处理。
  - 非常丑陋的界面设计和字体选择，每天看到眼瞎。
- Code Editor产品，长期无法修复滚轮会randomly跳转到光标的恶性bug。无法批量修改任务导致每次更改config都要手动一个一个地修改。没有integrate git而是自己开发了一个version control系统，无法atomically更改changes而是需要手动create version snapshot，而且回滚只能回滚到某一个版本的完全状态。
- 团队从PM lead到产品dev每个人都仿佛我们欠了他们八百万，scold用户是家常便饭。对于用户提出的feedback也是能推掉就推掉，以教育用户为主。但这可能也是所有内部工具团队的普遍状况，因为开发的产品并不是以市场为导向而是以老板为导向，用户的需求即使做了，在老板眼里也没有相应的impact。
- 从22年底到现在，新加坡没有预算开设新的机房，我们必须用有限的计算资源应对每天都会到来的数据需求，而且因为data pipeline任务没有支持global config的功能，经常有不熟悉数据开发的dev申请巨量的资源用光计算队列，每天的有相当多的时间浪费在发现这些illy-configured的任务，和删除cold data剩下空间之中。
  
1. 没有长期规划，项目随着老板的心情启用和废弃
投入很多心血的项目随着reorg被完全废弃推倒重来
1. 和底层完全脱节，没有人文关怀的管理层
Quickmart的管理层做出的决定往往令人血压升高，这也是我决定离开这家公司的重要原因之一。
- 堪比新闻联播的townhall
  我仍清晰地记得在被问到为什么如此苛刻地削减员工福利，甚至是开销并不大的饮料和零食时，某位chief车轱辘话了用了好几种方式表达“我们要培养cost-concious意识”。
1. 工作日趋琐碎
2. 员工没有morale

## 重新求职