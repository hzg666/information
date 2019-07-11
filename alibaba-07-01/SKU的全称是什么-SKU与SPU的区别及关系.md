Skip to content
 
Search or jump to…

Pull requests
Issues
Marketplace
Explore
 
@hzg666 
2
17 6 luban-hotman/interview-question
 Code  Issues 0  Pull requests 1  Projects 0  Wiki  Security  Insights
You’re editing a file in a project you don’t have write access to. Submitting a change to this file will write it to a new branch in your fork hzg666/interview-question, so you can send a pull request.
interview-question
/
doc
/
alibaba
/
alibaba-07-01
/
SKU的全称是什么-SKU与SPU的区别及关系.md
 

1
**SPU、SKU、item(淘宝叫item,京东叫product)是商品管理里面非常基础，又很容易被弄糊涂的三个概念。SPU 是由品牌+型号+关键属性构成的，在工作中，这个解释一直很有用**
2
​
3
首先要说的是，这三个概念不是像1+1=2这么具有确定性的东西，是具有相对性的。先记下这个词“相对性“；好了，让我们一个个的把概念弄明白。
4
​
5
一般我们查到SPU的定义是这样的：
6
​
7
**【SPU】**
8
​
9
SPU(Standard Product Unit)：标准化产品单元。 SPU是商品**信息聚合**的最小单位，是一组**可复用、易检索**的**标准化信息的集合**，该集合描述了一个产品的特性。
10
​
11
这里面有几个关键词:
12
​
13
**信息聚合：**意味着有识别度的信息被用来作为不同SPU的区分点；不是所有属性，使用的属性值是能够有区分度的关键属性值；
14
​
15
**易检索：**信息聚合与易检索这两个说明，是通过关键属性+属性值的聚合来实现易检索这个目的；目的与使用场景相关联，并非万古不变；哪些属性和属性值会被选为区分SPU的关键属性是会随着场景变化的； 但对于一些场景，已经是共识；比如电商销售，对于标品基本都会选择品牌+型号+关键属性；这也是很多年前我所得到的解释。
16
​
17
**标准化的信息集合：**说明SPU的本质是信息集合，是一个**抽象概念**，并非是看得见的东西。比如格力空调 KFR-25GW/E;
18
​
19
指的不是放在房子里面，可以看见的那个实物空调，而是这样的一个信息集合：
20
​
21
格力KFR-25GW/E 其中格力表示品牌名，K表示房间空调器，F表示分体式，R表示热泵型，25表示制冷量是2500瓦，G表示挂壁式，W表示室外机代号，E表示冷静王系列。作为SPU来说，这是一个信息集合的架子，对应不到一个具体的实物，有点类似面向对象概念里面“类“的概念；但是通过这些信息框定一批具有此信息特征的产品；
22
​
23
**【item】**
24
​
25
item更多的是用来指“单品”的概念，注意的是单品也是一个**抽象概念**；
26
​
27
它也是一个**场景概念**；可以指在一定场景下**讨论/交易**的最小单元；多数场景下指一个SKU； 
28
​
29
比如，在有些服装批发，一个单品可能会只一个颜色的商品，这个颜色的商品会有多个尺码； 或者在一些情况下，买家不关心颜色也不关心尺码，这时候一个单品可能就会是商品的概念；哪怕它有多个颜色尺码；
30
​
31
**【SKU】**
32
​
33
SKU=stock keeping unit(库存量单位) SKU即库存进出计量的单位（买家购买、商家进货、供应商备货、工厂生产都是依据SKU进行的），在服装、鞋类商品中使用最多最普遍。 例如纺织品中一个SKU通常表示：规格、颜色、款式。 SKU是物理上不可分割的最小存货单元。也就是说一款商品，可以根据SKU来确定具体的货物存量。 sku 属性(会影响到库存和价格的属性, 又叫销售属性)---规格
34
​
35
**注意的是，SKU仍然是一个具有场景性，同时也有相对性的概念；**
36
​
37
SKU是物理上不可分割的最小存货单元。在使用时要根据不同业态，不同管 理模式来处理。比如一香烟是50条，一条里有十盒，一盒中有20支，这些单位就要根据不同的需要来设定SKU。比如仓储批发式大卖场，一定是按照一箱来设 定的。普通大卖场一定是按照条来设定的。烟酒专卖店一定是按照盒来设定的。过去上海等地的街边小店一定是按一支来设定的。这样一支就是烟的最小零售单位 但要根据自己的业态和服务模式来设定。
@hzg666
Propose file change
Commit summary 
Update SKU的全称是什么-SKU与SPU的区别及关系.md
Optional extended description
Add an optional extended description…
  
 Waiting for your fork…
© 2019 GitHub, Inc.
Terms
Privacy
Security
Status
Help
Contact GitHub
Pricing
API
Training
Blog
About
