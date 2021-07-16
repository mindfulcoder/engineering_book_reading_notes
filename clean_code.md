# 整洁代码精粹

## 一、概述

### 1. 学习整洁代码的原因

学习整洁代码有两种原因：第一，你是个程序员；第二，你想成为更好的程序员。

学习完本课程以后，你不但能说出好代码和糟糕的代码之间的差异，而且也知道如何将糟糕的代码改成好代码。

### 2. 代码长存

有人也许会以为，随着技术与平台的发展，代码不再需要人工编写。

扯淡！我们永远抛不掉代码，因为代码呈现了需求的细节，我们永远无法抛弃必要的精确性——所以代码永存。

### 3. 糟糕的代码

你是否曾为糟糕的代码所深深困扰？那么你为什么要写糟糕的代码呢？

是想快点完成吗？是要赶时间吗？

我们都曾经瞟一眼自己亲手造成的混乱，决定弃之而不顾，走向新一天。

我们都曾经说过有朝一日再回头清理。

当然，事情的结局都是：稍后等于永不（Later equals never）。

### 4. 混乱的代价

只要你干过两三年编程，就有可能曾被某人的糟糕的代码绊倒过。

有些团队在项目初期进展迅速，但有那么一两年的时间却慢如蜗行。

这团乱麻越来越大，再也无法理清，最后束手无策。

随着混乱的增加，团队生产力也持续下降，趋向于零。

当生产力下降时，管理层就只有一件事可做了：增加更多人手到项目中，期望提升生产力。

可是新人并不熟悉系统的设计，团队背负着提升生产力的可怕压力。于是，他们制造更多的混乱，驱动生产力向零那端不断下降。

### 5. 华丽新设计

在烂代码的折磨下，开发团队造反了，他们要求推倒重来。

管理层不愿意，但他们也无计可施。于是，他们只好授权开发团队去做一套全新设计。

Tiger Team成立了，只有最优秀、最聪明的家伙被选中，其余人等则继续维护现有系统。

新团队必须搭建一套新系统，不但要能实现旧系统的所有功能，而且还得跟上对旧系统的持续改动。

在新系统功能足以抗衡旧系统之前，管理层不会替换掉旧系统。

这种竞赛可能会持续极长时间，到了完成的时候，新团队的老成员早已不知去向，而现有成员则要求重新设计一套新系统，因为这套系统太烂了。

假使你经历过哪怕是一小段这种事，那么你一定知道，花时间保持代码整洁不但有关效率，还有关生存。

### 6. 态度

程序员经常把烂代码归咎于那些愚蠢的经理、苛求的用户、没用的营销方式。不过，问题的本质往往是程序员缺乏专业态度。

### 7. 什么是整洁代码

Bjarne Stroustrup，C++语言发明者，C++Programming Language（中译版《C++程序设计语言》）一书作者。

> 我喜欢优雅和高效的代码。代码逻辑应当直截了当，叫缺陷难以隐藏；尽量减少依赖关系，使之便于维护；依据某种分层战略完善错误处理代码；性能调至最优，省得引诱别人做没规矩的优化，搞出一堆混乱来。整洁的代码只做好一件事。

Grady Booch，Object Oriented Analysis and Design with Applications（中译版《面向对象分析与设计》）一书作者。

> 整洁的代码简单直接。整洁的代码如同优美的散文。整洁的代码从不隐藏设计者的意图，充满了干净利落的抽象和直截了当的控制语句。

Dave Thomas，OTI 公司创始人，Eclipse 战略教父。

> 整洁的代码应可由作者之外的开发者阅读和增补。它应当有单元测试和验收测试。它使用有意义的命名。它只提供一种而非多种做一件事的途径。它只有尽量少的依赖关系，而且要明确地定义和提供清晰、尽量少的 API。代码应通过其字面表达含义，因为不同的语言导致并非所有必需信息均可通过代码自身清晰表达。

Michael Feathers，Working Effectively with Legacy Code（中译版《修改代码的艺术》）一书作者。

> 我可以列出我留意到的整洁代码的所有特点，但其中有一条是根本性的。整洁的代码总是看起来像是某位特别在意它的人写的。几乎没有改进的余地。代码作者什么都想到了，如果你企图改进它，总会回到原点，赞叹某人留给你的代码——全心投入的某人留下的代码。

Ron Jeffries，Extreme Programming Installed（中译版《极限编程实施》）以及 Extreme Programming Adventures in C#（中译版《C#极限编程探险》）作者。

> Ron 初入行就在战略空军司令部（Strategic Air Command）编写 Fortran 程序，此后几乎在每种机器上编写过每种语言的代码。他的言论值得咀嚼。

Ward Cunningham，Wiki 发明者，eXtreme Programming （极限编程）的创始人之一，Smalltalk 语言和面向对象的思想领袖。所有在意代码者的教父。

> 如果每个例程都让你感到深合己意，那就是整洁代码。如果代码让编程语言看起来像是专为解决那个问题而存在，就可以称之为漂亮的代码。

### 8.  童子军军规

借用美国童子军一条简单的军规，应用到我们的专业领域：

> 让营地比你来时更干净。

如果每次签入时，代码都比签出时干净，那么代码就不会腐坏。

你想要为一个代码随时间流逝而越变越好的项目工作吗？你还能相信有其他更专业的做法吗？难道持续改进不是专业性的内在组成部分吗？



## 二、有意义的命名

### 1. 好的名字能揭示意图

名副其实说起来简单，但是实践起来很难，应该严肃对待。

良好的命名应该揭示内涵，如果名称需要注释来补充，那就不算是名副其实。

```java
int d; // elapsed time in days
```

你知道上面的d代表什么吗？

```java
int elapsedTimeInDays;
int daysSinceCreation;
int daysSinceModification;
int fileAgeInDays;
```

良好的命名名称能让人更容易理解和修改代码。

```java
public List<int[]> getThem() {
  List<int[]> list1 = new ArrayList<int[]>();
  for (int[] x : theList)
    if (x[0] == 4)
      list1.add(x);
  return list1;
}
```

上述代码可能让你产生如下疑问：

1. theList 中是什么类型的东西？
2. theList 零下标条目的意义是什么？
3. 值 4 的意义是什么？
4. 我怎么使用返回的列表？

又如：

```java
public List<int[]> getFlaggedCells() {
  List<int[]> flaggedCells = new ArrayList<int[]>();
  for (int[] cell : gameBoard)
  if (cell[STATUS_VALUE] == FLAGGED)
    flaggedCells.add(cell);
  return flaggedCells;
}
```

V.S

```java
public List<Cell> getFlaggedCells() {
  List<Cell> flaggedCells = new ArrayList<Cell>();
  for (Cell cell : gameBoard)
    if (cell.isFlagged())
      flaggedCells.add(cell);
  return flaggedCells;
}
```

### 2. 避免传递错误的信息

- 避免在代码中留下错误，或者容易混淆的信息。

```java
int hp,ibm,redhat = 0; 
Map accountList=new HashMap()
```

- 避免使用只有细微区别的名字。


```java
XYZControllerForEfficientHandlingOfStrings
XYZControllerForEfficientStorageOfStrings
```

- 永远不要使用L和O作变量名。

```java
int a = l;
if ( O == l )
  a = O1;
else
  l = 01;
```

### 3. 使用便于区分的名称

- 在变量名后面加数字来区分是不够的。


以数字系列命名（a1、a2，……aN）是依义命名的对立面。

```java
public static void copyChars(char a1[], char a2[]) {
  for (int i = 0; i < a1.length; i++) {
    a2[i] = a1[i];
  }
}
```

- 太泛的概念不足以提供区分度。


```java
ProductInfo v.s. ProductData v.s. ProductObject
```

- 遵循约定俗成。

```java
xxxxFactory
xxxxService
xxxxServiceImpl
```

### 4. 使用可以朗读的名称

- 软件工程师一种社会活劢，如果名称不能读出来，讨论代码时就会显得很傻，以至于大家不愿意讨论代码。

```java
class DtaRcrd102 {
  private Date genymdhms;
  private Date modymdhms;
  private final String pszqint = ”102”;
  /* … */
};
```

V.S

```java
class Customer {
  private Date generationTimestamp;
  private Date modificationTimestamp;;
  private final String recordId = ”102”;
  /* … */
};
```

### 5. 使用可搜索的名称

- 用一两个字符作变量名，会让名称很难搜索，也就很难定位问题。
- 用一两个字符作为变量名，只能用于函数的本地变量，并且函数要足够短小。

```java
for (int j=0; j<34; j++) {
  s += (t[j]*4)/5;
}
```

V.S

```java
int realDaysPerIdealDay = 4;
const int WORK_DAYS_PER_WEEK = 5;
int sum = 0;
for (int j=0; j < NUMBER_OF_TASKS; j++) {
  int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
  int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
  sum += realTaskWeeks;
}
```

### 6. 避免名字编码

- 避免匈牙利命名法

```java
PhoneNumber phoneString; // name not changed when type changed!
```

- 避免成员变量前缀


```java
public class Part {
  private String m_dsc; // The textual description
  void setName(String name) {
    m_dsc = name;
  }
}
```

V.S

```java
public class Part {
  String description;
  void setDescription(String description) {
    this.description = description;
  }
}
```

- 避免接口类型前缀

> IShapeFactory v.s. ShapeFactory ShapeFactoryImp

### 7. 避免思维映射

- 读者不用在头脑中保存一个“映射表”才能知道名字的具体含义。
- 聪明的程序员和专业的程序员的最大区别，就是专业的程序员知道“清晰才是王道。

```java
String h=“www.baidu.com“
String u=“http://www.baidu.com“
```

v.s.

```java
String host=“www.baidu.com“
String url=“https://www.baidu.com“
```

### 8. 类命名

类名和对象名应该是名词或名词短语，如 Customer、WikiPage、Account 和 AddressParser。避免使用 Manager、Processor、Data 或 Info 这样的类名。类名不应当是动词。

### 9. 方法命名

方法名应当是动词或动词短语，如 postPayment、deletePage 或 save。

属性访问器、修改器和断言应该根据其值命名，并按照 Javabean 规范要求加上 get、set 和 is 前缀。

```java
string name = employee.getName();
customer.setName(”mike”);
if (paycheck.isPosted())…
```

重载构造器时，使用描述了参数的静态工厂方法名。例如，

```java
Complex fulcrumPoint = Complex.FromRealNumber(23.0);
```

通常好于

```java
Complex fulcrumPoint = new Complex(23.0);
```

### 10. 别扮可爱

如果名称太耍宝，那就只有同作者一般有幽默感的人才能记得住，而且还是在他们记得那个笑话的时候才行。

例如，别用 whack( )表示 kill( )。用 eatMyShorts( )来表示 abort( )。

### 11. 每个概念对应一个词

例如，一旦选择一个词来表示“查询”的概念，那么最好始终用它。

fetch, retrieve, get, select, query, find, search

### 12. 别用双关语

避免将同一单词用于不同目的。同一术语用于不同概念，基本上就是双关语了。

> add //math operation
> add //append

### 13. 使用专业案领名词

使用解决方案领域名词，如科学术语、专业术语、算法名称、设计模式名称等来命名。

### 14. 使用业务领域的名词

使用来自于业务领域而来命名。至少，负责维护代码的程序员可以去请教业务领域专家了。

### 15. 添加有意义的语境

- 尽量利用有意义的上下文环境。


```java
public class HttpRequest { 
    private String host; 
    private int port; 
    private String potocol; 
}
```

### 16. 不要添加没用的语境

- 避免重复上下文环境提供的信息。

```java
public class HttpRequest { 
    private String httpRequestHost; 
    private int httpRequestPort; 
    private String httpRequestPotocol; 
}
```

### 17. 关于命名的总结

为了良好的命名而修改名字是一种代码概述工作。如果名称改得更好，那么所有的开发人员都会感激你。



## 三、函数结构

### 1. 函数应该小，越小越好！

- 在1980年代，普遍认为单个函数不应该超过20行。

  理由是当时的显示器VT100一个屏幕叧能显示20行。

- 现在我们认为一个好的函数不应该超过10行。

### 2. 函数应该叧做一件事情！

- 函数应该叧做一件事情，并且把它做好。
- 如果函数包含多个段落，那么它就不止做了一件事情。
- 如果函数包含多个抽象层次，那么他也不止做一件事情。

### 3. 提取小函数，直到你放弃！
- 从大函数中抽取小函数，直到你再也提取不出为止。

### 4. 关于提取函数的担忧

- 小函数太多会丌会导致难于定位代码？
  - 小函数需要有良好的命名。
  - 函数名就像路标，有好的名字，则越多越清晰。

- 函数太多会丌会导致程序运行效率低下？
  - 对于大多数程序而言，代码整洁排在第一优先级。
  - 现代的编译器、运行时和硬件已经使这种差别忽略不计。

- 把函数变小是丌是浪费时间？
  - 个人虽然花了更多时间，但是对整个团队和维护工作来说却节省了时间；
  - 维护成本比开发成本高

### 5. 函数的抽象层级

-  自上而下法则

 我们在描述问题时，通常是按照从抽象到具体的顺序，逐层细化，直到无需解释的基本概念为止。  类似的，函数调用的入口应该是一个较抽象函数，它的内部调用更加具体的小函数，这些小函数内部又调用更具体的其他小函数，直到每一步都是一目了然的操作为止。

### 6. 消除switch语句

- switch语句天然地违背了单一职责原则，但却不可避免；
- 可以将每一个case抽取为一个独立的函数来简化switch语句；
- 可以利用面向对象语言的的多态特性和工厂模式来减少switch语句使用；

```java
public Money calculatePay(Employee e)
throws InvalidEmployeeType {
    switch (e.type) {
      case COMMISSIONED:
        return calculateCommissionedPay(e);
      case HOURLY:
        return calculateHourlyPay(e);
      case SALARIED:
        return calculateSalariedPay(e);
      default:
        throw new InvalidEmployeeType(e.type);
    }
  }
```

如果上述代码不止一次出现，则可以考虑重构为工厂。

```java
public abstract class Employee {
  public abstract boolean isPayday();
  public abstract Money calculatePay();
  public abstract void deliverPay(Money pay);
}
-----------------
public interface EmployeeFactory {
  public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}
-----------------
public class EmployeeFactoryImpl implements
      EmployeeFactory {
  public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
    switch (r.type) {
      case COMMISSIONED:
        return new CommissionedEmployee(r) ;
      case HOURLY:
        return new HourlyEmployee(r);
      case SALARIED:
        return new SalariedEmploye(r);
      default:
        throw new InvalidEmployeeType(r.type);
    }
  }
}
```

### 7. 使用描述性的函数名

函数名称描述了函数做的事。

函数越短小、功能越集中，就越便于取个好名字。

别害怕长名称。长而具有描述性的名称，要比短而令人费解的名称好。长而具有描述性的名称，要比描述性的长注释好。

选择描述性的名称能理清你关于模块的设计思路，并帮你改进之。

使用与模块名一脉相承的短语、名词和动词给函数命名。

### 8. 函数参数

- 良好的参数命名
  - 函数名称能揭示内涵。
  - 使用劢词戒者劢词加名词作为函数名。
  - 参数名称要能体现意图。

- 参数数量
  - 没有参数最好，1个也行，2个也可以，不要超过3个。
  - 不能有boolean类型的参数。
  - 不能有输出参数。
  - 不要有可以为Null的参数，避免过多的Null判断。
  - 如果参数很多，将参数变成数组戒者一个单独的类。

### 9. 避免副作用

- 函数另做一件事情，这件事情是由函数名称所定义的，不能“顺便”做其他事情。


```java
public class UserValidator {
  private Cryptographer cryptographer;

  public boolean checkPassword(String userName, String password) {
    User user = UserGateway.findByName(userName);
    if (user != User.NULL) {
      String codedPhrase = user.
      getPhraseEncodedByPassword();
      String phrase = cryptographer.decrypt(codedPhrase, password);
      if ("Valid Password".equals(phrase)) {
        Session.initialize();
        return true;
      }
    }
    return false;
  }
}
```

副作用就在于对 Session.initialize( )的调用。checkPassword 函数，顾名思义，就是用来检查密码的。该名称并未暗示它会初始化该次会话。所以，当某个误信了函数名的调用者想要检查用户有效性时，就得冒抹除现有会话数据的风险。

- 避免输出参数

输出参数是指改变输入参数的状态，而该参数在同一抽象等级的其他操作中任然会被使用。如果要修改状态，只能能修改自己拥有的对象的状态。

```java
public void appendFooter(StringBuffer report)
```

### 10. 命令与查询分离

函数的职责应该是以下的其中之一，而不是同时包含多种: 

1. 查询对象的状态 ；
2. 修改对象的状态，戒者通过参数生成新的对象；

考虑如下代码：

```java
public boolean set(String attribute, String value);
```

其作用是设置属性值，如果成功则返回true，如果没有改属性则返回false。这样导致调用代码如：

```java
 if (set("username", "unclebob"))... 
```

从调用者角度看，这到底是在比较username是否是unclebob，还是在设置username为unclebob？

如果改为如下的代码则不会出现这种情况，并且实现了“命令不查询分离：

```java
if (attributeExists(”username”)) {
  setAttribute(”username”, ”unclebob”);
  …
}
```

### 11. 异常优于错误代码

- 函数如果返回错误代码，则调用者必须处理返回码，不但造成了耦合，而且违背了“命令不查询分离的原则”。
- 如果返回码必须被处理，则异常处理代码和业务代码混为一团，调用者违背“单一职责”原理。

```java
   if (deletePage(page) == E_OK)
```

当返回错误码时，就是在要求调用者立刻处理错误：

```java
if (deletePage(page) == E_OK) {
  if (registry.deleteReference(page.name) == E_OK) {
    if (configKeys.deleteKey(page.name.makeKey()) == E_OK){
      logger.log("page deleted");
    } else {
      logger.log("configKey not deleted");
    }
  } else {
    logger.log("deleteReference from registry failed");
  }
} else {
  logger.log("delete failed");
  return E_ERROR;
}
```

### 12. 抽离 Try/Catch 代码块

Try/catch 代码块丑陋不堪。它们搞乱了代码结构，把错误处理与正常流程混为一谈。最好把 try 和 catch 代码块的主体部分抽离出来，另外形成函数。

```java
public void delete(Page page) {
  try {
    deletePageAndAllReferences(page);
  }
  catch (Exception e) {
    logError(e);
  }
}

private void deletePageAndAllReferences(Page page) throws Exception {
  deletePage(page);
  registry.deleteReference(page.name);
  configKeys.deleteKey(page.name.makeKey());
}

private void logError(Exception e) {
  logger.log(e.getMessage());
}
```

### 13. 错误处理就是一种职责

函数应该只做一件事。错误处理就是一件事。因此，处理错误的函数不该做其他事。

这意味着如果关键字 try 在某个函数中存在，它就该是这个函数的第一个单词，而且在 catch/finally 代码块后面也不该有其他内容。

### 14. 依赖磁铁

返回错误码通常暗示某处有个类或是枚举，定义了所有错误码。

```java
public enum Error {
  OK,
  INVALID,
  NO_SUCH,
  LOCKED,
  OUT_OF_RESOURCES,
  WAITING_FOR_EVENT;
}
```

这样的类就是一块依赖磁铁（dependency magnet）；其他许多类都得导入和使用它。

使用异常替代错误码，新异常就可以从异常类派生出来，无需重新编译或重新部署。

### 15. 避免重复

重复可能是软件中一切邪恶的根源。许多原则与实践规则都是为控制与消除重复而创建。自程序发明以来，软件开发领域的所有创新都是在不断尝试从源代码中消灭重复。

### 16. 最少知道原则（Law of Demeter）

- 无论逻辑多么复杂，都应当将逻辑封装在类的内部，对外提供统一的public方法，而不暴露调用者不需要知道的内部方法。

```java
o.getX().getY().getZ().doSomething()
```

V.S

```java
public void doSomething() { 
return this.getX().getY.getZ().doSomething(); 
} 
//caller
o. doSomething();
```

- 如果违背，则一方面调用方复杂度增加，另外一方面造成代码和紧耦合。

### 16. 结构化编程

结构化编程要求在每个函数中只该有一个出口。

只要函数保持短小，偶尔出现的 return、break 或 continue 语句没有坏处，甚至还比单入单出原则更具有表达力。

### 17. 关于函数的小结

优秀的程序员把系统当作故事来讲，而不是当作程序来写。

每个系统都是使用某种领域特定语言搭建，而这种语言是程序员设计来描述那个系统的。函数是语言的动词，类是名词。

## 四、注释

注释是一种必须的恶。若编程语言足够有表达力，或者我们擅长用编程语言来表达意图，就不那么需要注释。

### 1. 注释不能美化糟糕的代码

- 如果你觉得一段代码很难懂，不要尝试给他加注释，而要重构这段代码使他变得清晰。

### 2. 不依靠注释，而靠代码自身来阐明意图

```java
// Check to see if the employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) &&
    (employee.age > 65))
```

V.S

```java
if (employee.isEligibleForFullBenefits())
```

### 3. 好的注释

#### 3.1 法律法规相关注释

例如，版权及著作权声明就是必须和有理由在每个源文件开头注释处放置的内容。

```java
// Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
// Released under the terms of the GNU General Public License version 2 or later.
```

#### 3.2 重要的提示性信息

有时，用注释来提供基本信息也有其用处。例如，以下注释解释了某个抽象方法的返回值：

```java
// Returns an instance of the Responder being tested.
protected abstract Responder responderInstance();
```

这类注释有时管用，但更好的方式是尽量利用函数名称传达信息。

下例稍好一些：

```java
// format matched kk:mm:ss EEE, MMM dd, yyyy
Pattern timeMatcher = Pattern.compile(
  “\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*”);
```

#### 3.3 阐明意图

有时，注释不仅提供了有关实现的有用信息，而且还提供了某个决定后面的意图。

```java
public int compareTo(Object o)
{
  if(o instanceof WikiPagePath)
  {
    WikiPagePath p = (WikiPagePath) o;
    String compressedName = StringUtil.join(names, “”);
    String compressedArgumentName = StringUtil.join(p.names, “”);
    return compressedName.compareTo(compressedArgumentName);
  }
  return 1; // we are greater because we are the right type.
}
```

下面的例子甚至更好。你也许不同意程序员给这个问题提供的解决方案，但至少你知道他想干什么。

```java
public void testConcurrentAddWidgets() throws Exception {
  WidgetBuilder widgetBuilder =
    new WidgetBuilder(new Class[]{BoldWidget.class});
    String text = ”’’’bold text’’’”;
    ParentWidget parent =
      new BoldWidget(new MockWidgetRoot(), ”’’’bold text’’’”);
    AtomicBoolean failFlag = new AtomicBoolean();
    failFlag.set(false);

    //This is our best attempt to get a race condition
    //by creating large number of threads.
    for (int i = 0; i < 25000; i++) {
      WidgetBuilderThread widgetBuilderThread =
        new WidgetBuilderThread(widgetBuilder, text, parent, failFlag);
      Thread thread = new Thread(widgetBuilderThread);
      thread.start();
    }
    assertEquals(false, failFlag.get());
  }
```

#### 3.4 澄清容易产生的误解

有时，注释把某些晦涩难明的参数或返回值的意义翻译为某种可读形式，也会是有用的。

```java
public void testCompareTo() throws Exception
{
  WikiPagePath a = PathParser.parse("PageA");
  WikiPagePath ab = PathParser.parse("PageA.PageB");
  WikiPagePath b = PathParser.parse("PageB");
  WikiPagePath aa = PathParser.parse("PageA.PageA");
  WikiPagePath bb = PathParser.parse("PageB.PageB");
  WikiPagePath ba = PathParser.parse("PageB.PageA");

  assertTrue(a.compareTo(a) == 0);    // a == a
  assertTrue(a.compareTo(b) != 0);    // a != b
  assertTrue(ab.compareTo(ab) == 0);  // ab == ab
  assertTrue(a.compareTo(b) == -1);   // a < b
  assertTrue(aa.compareTo(ab) == -1); // aa < ab
  assertTrue(ba.compareTo(bb) == -1); // ba < bb
  assertTrue(b.compareTo(a) == 1);    // b > a
  assertTrue(ab.compareTo(aa) == 1);  // ab > aa
  assertTrue(bb.compareTo(ba) == 1);  // bb > ba
}
```

当然，这也会冒阐释性注释本身就不正确的风险。所以，在写这类注释之前，考虑一下是否还有更好的办法，然后再加倍小心地确认注释正确性。

#### 3.5 警示可能产生的后果

有时，用于警告其他程序员会出现某种后果的注释也是有用的。

```java
// Don't run unless you
// have some time to kill.
public void _testWithReallyBigFile()
{
  writeLinesToFile(10000000);

  response.setBody(testFile);
  response.readyToSend(this);
  String responseString = output.toString();
  assertSubString("Content-Length: 1000000000", responseString);
  assertTrue(bytesSent > 1000000000);
}
```

```java
public static
  SimpleDateFormat makeStandardHttpDateFormat()
{
  //SimpleDateFormat is not thread safe,
  //so we need to create each instance independently.
  SimpleDateFormat df = new SimpleDateFormat(”EEE, dd MMM  yyyy HH:mm:ss z”);
  df.setTimeZone(TimeZone.getTimeZone(”GMT”));
  return df;
}
```

#### 3.6 提醒待办事项

有时，有理由用//TODO 形式在源代码中放置要做的工作列表。

```java
//TODO-MdM these are not needed
// We expect this to go away when we do the checkout model
protected VersionInfo makeVersion() throws Exception
{
  return null;
}
```

#### 3.7 强调重要性

注释可以用来放大某种看来不合理之物的重要性。

```java
String listItemContent = match.group(3).trim();
// the trim is real important.  It removes the starting
// spaces that could cause the item to be recognized
// as another list.
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));
```

#### 3.8  Javadoc风格的接口定义

没有什么比被良好描述的公共 API 更有用和令人满意的了。标准 Java 库中的 Javadoc 就是一例。没有它们，写 Java 程序就会变得很难。

### 4.坏的注释

#### 4.1 自言自语的注释

如果只是因为你觉得应该或者因为过程需要就添加注释，那就是无谓之举。如果你决定写注释，就要花必要的时间确保写出最好的注释。

```java
public void loadProperties()
{
  try
  {
  String propertiesPath = propertiesLocation +
    ”/” + PROPERTIES_FILE;
  FileInputStream propertiesStream = new
    FileInputStream(propertiesPath);
  loadedProperties.load(propertiesStream);
  }
  catch(IOException e)
  {
    // No properties files means all defaults are loaded
  }
}
```

#### 4.2 多余的注释

代码清单展示的简单函数，其头部位置的注释全属多余。读这段注释花的时间没准比读代码花的时间还要长。

```java
// Utility method that returns when this.closed
    is true. Throws an exception
// if the timeout is reached.
public synchronized void waitForClose(final long timeoutMillis)
throws Exception
{
  if(!closed)
  {
      wait(timeoutMillis);
      if(!closed)
        throw new Exception("MockResponseSender could not be closed");
  }
}
```

#### 4.3 误导性注释

有时，尽管初衷可嘉，程序员还是会写出不够精确的注释。

这种误导信息可能导致其他程序员快活地调用这个函数，然后发现自己陷于调试困境之中。

#### 4.4 遵循规范注释

有些“规范”类似于传说。例如，所谓每一行代码都要有注释的规矩就是是愚蠢可笑的。这类注释让代码变得散乱，满口胡言，令人迷惑不解。

```java
/**
*
* @param title The title of the CD
* @param author The author of the CD
* @param tracks The number of tracks on the CD
* @param durationInMinutes The duration of the CD in minutes
*/
public void addCD(String title, String author,
                  int tracks, int durationInMinutes) {
  CD cd = new CD();
  cd.title = title;
  cd.author = author;
  cd.tracks = tracks;
  cd.duration = duration;
  cdList.add(cd);
}
```

#### 4.5 日志式注释

有人会在每次编辑代码时，在模块开始处添加一条注释。这类注释就像是一种记录每次修改的日志。我见过满篇尽是这类日志的代码模块。

```java
* Changes (from 11-Oct-2001)
* --------------------------
* 11-Oct-2001 : Re-organised the class and moved it to new package
*               com.jrefinery.date (DG);
* 05-Nov-2001 : Added a getDescription() method, and eliminated NotableDate
*               class (DG);
* 12-Nov-2001 : IBD requires setDescription() method, now that NotableDate
*               class is gone (DG);  Changed getPreviousDayOfWeek(),
*               getFollowingDayOfWeek() and getNearestDayOfWeek() to correct
*               bugs (DG);
* 05-Dec-2001 : Fixed bug in SpreadsheetDate class (DG);
* 29-May-2002 : Moved the month constants into a separate interface
*               (MonthConstants) (DG);
* 27-Aug-2002 : Fixed bug in addMonths() method, thanks to N???levka Petr (DG);
* 03-Oct-2002 : Fixed errors reported by Checkstyle (DG);
* 13-Mar-2003 : Implemented Serializable (DG);
* 29-May-2003 : Fixed bug in addMonths method (DG);
* 04-Sep-2003 : Implemented Comparable.  Updated the isInRange javadocs (DG);
* 05-Jan-2005 : Fixed bug in addYears() method (1096282) (DG);
```

很久以前，在模块开始处创建并维护这些记录还算有道理。那时，我们还没有源代码控制系统可用。如今，这种冗长的记录只会让模块变得凌乱不堪，应当全部删除。

#### 4.6 废话注释

有时，你会看到纯然是废话的注释。它们对于显然之事喋喋不休，毫无新意。

```java
/**
* Default constructor.
*/
protected AnnualDateRule() {
}
```

对吧？再看看这个：

```java
/** The day of the month. */
    private int dayOfMonth;
```

这样的废话模范：

```java
/**
  * Returns the day of the month.
  *
  * @return the day of the month.
  */
public int getDayOfMonth() {
  return dayOfMonth;
}
```

Javadoc 也可能是废话。下列 Javadoc（来自某知名开源库）的目的是什么？

```java
/** The name. */
private String name;

/** The version. */
private String version;

/** The licenceName. */
private String licenceName;

/** The version. */
private String info;
```

#### 4.7 能用函数或变量时就别用注释

看看以下代码概要：

```java
// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```

可以改成以下没有注释的版本：

```java
ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```

#### 4.8  位置标记

有时，程序员喜欢在源代码中标记某个特别位置。例如，最近我在程序中看到这样一行：

```java
// Actions //////////////////////////////////
```

#### 4.9 括号后面的注释



有时，程序员会在括号后面放置特殊的注释，例如你想标记右括号，其实应该做的是缩短函数。

```java
public class wc {
  public static void main(String[] args) {
    BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
    String line;
    int lineCount = 0;
    int charCount = 0;
    int wordCount = 0;
    try {
      while ((line = in.readLine()) != null) {
        lineCount++;
        charCount += line.length();
        String words[] = line.split("\\W");
        wordCount += words.length;
      } //while
      System.out.println("wordCount = " + wordCount);
      System.out.println("lineCount = " + lineCount);
      System.out.println("charCount = " + charCount);
    } // try
    catch (IOException e) {
      System.err.println("Error:" + e.getMessage());
    } //catch
  } //main
}
```

#### 4.10 开发者署名

```java
/* Added by Rick */
```

源代码控制系统非常善于记住是谁在何时添加了什么。没必要用那些小小的签名搞脏代码。

#### 4.11 注释掉的代码

直接把废弃代码注释掉是讨厌的做法。别这么干！

```java
  InputStreamResponse response = new InputStreamResponse();
  response.setBody(formatter.getResultStream(), formatter.getByteCount());
// InputStream resultsStream = formatter.getResultStream();
// StreamReader reader = new StreamReader(resultsStream);
// response.setContent(reader.read(formatter.getByteCount()));
```

其他人不敢删除注释掉的代码。他们会想，代码依然放在那儿，一定有其原因，而且这段代码很重要，不能删除。注释掉的代码堆积在一起，就像破酒瓶底的渣滓一般。

#### 4.12 HTML 注释

源代码注释中的 HTML 注释的让代码难以读懂。。

如果注释将由某种工具抽取出来，呈现到网页，那么该是工具负责给注释加上 HTML 标签。

```java
/**
* Task to run fit tests.
* This task runs fitnesse tests and publishes the results.
* <p/>
* <pre>
* Usage:
* &lt;taskdef name=&quot;execute-fitnesse-tests&quot;
*     classname=&quot;fitnesse.ant.ExecuteFitnesseTestsTask&quot;
*     classpathref=&quot;classpath&quot; /&gt;
* OR
* &lt;taskdef classpathref=&quot;classpath&quot;
*             resource=&quot;tasks.properties&quot; /&gt;
* <p/>
* &lt;execute-fitnesse-tests
*     suitepage=&quot;FitNesse.SuiteAcceptanceTests&quot;
*     fitnesseport=&quot;8082&quot;
*     resultsdir=&quot;${results.dir}&quot;
*     resultshtmlpage=&quot;fit-results.html&quot;
*     classpathref=&quot;classpath&quot; /&gt;
* </pre>
*/
```

#### 4.13 非本地信息

假如你一定要写注释，请确保它描述了离它最近的代码。别在本地注释的上下文环境中给出系统级的信息。

```java
/**
* Port on which fitnesse would run. Defaults to 8082.
*
* @param fitnessePort
*/
public void setFitnessePort(int fitnessePort)
{
  this.fitnessePort = fitnessePort;
}
```

#### 4.14  信息过多

别在注释中添加有趣的历史性话题或者无关的细节描述。

```java
/*
    RFC 2045 - Multipurpose Internet Mail Extensions (MIME)
    Part One: Format of Internet Message Bodies
    section 6.8.  Base64 Content-Transfer-Encoding
    The encoding process represents 24-bit groups of input bits as output
    strings of 4 encoded characters. Proceeding from left to right, a
    24-bit input group is formed by concatenating 3 8-bit input groups.
    These 24 bits are then treated as 4 concatenated 6-bit groups, each
    of which is translated into a single digit in the base64 alphabet.
    When encoding a bit stream via the base64 encoding, the bit stream
    must be presumed to be ordered with the most-significant-bit first.
    That is, the first bit in the stream will be the high-order bit in
    the first 8-bit byte, and the eighth bit will be the low-order bit in
    the first 8-bit byte, and so on.
  */
```

#### 4.15 不明显的联系

注释及其描述的代码之间的联系应该显而易见。如果你不嫌麻烦要写注释，至少让读者能看着注释和代码，并且理解注释所谈何物。

```java
   /*
    * start with an array that is big enough to hold all the pixels
    * (plus filter bytes), and an extra 200 bytes for header info
    */
   this.pngBytes = new byte[((this.width + 1) * this.height * 3) + 200];
```

过滤器字节是什么？与那个+1 有关系吗？或与\*3 有关？还是与两者皆有关？为什么用 200？注释的作用是解释未能自行解释的代码。如果注释本身还需要解释，就太遗憾了。

#### 4.16 函数头

短函数不需要太多描述。为只做一件事的短函数选个好名字，通常要比写函数头注释要好。

#### 4.17 非公共代码中的 Javadoc

虽然 Javadoc 对于公共 API 非常有用，但对于不打算作公共用途的代码就令人厌恶了。



## 五、格式

### 1. 代码的格式是影响代码可读性重要因素

先明确一下，代码格式很重要。代码格式不可忽略，必须严肃对待。代码格式关乎沟通，而沟通是专业开发者的头等大事。

### 2. 在一个团队内应该有统一的格式标准

- 开发团队应该选择一套大家都认可的格式标准。
- 最好利用自动化工具格式代码。

### 2. 垂直格式

#### 2.1 单个源文件的大小不应该超过300行

- 如果超过300行，通常意味着其职责过多，应该考虑拆分。

#### 2.2 重要的功能因位于源文件头部

- 阅读代码时通常是采用自上而下、从左到右的顺序。
- 抽象程度越高的函数和功能模块的入口应该放在靠文件头的位置。

#### 2.3 相关的概念垂直方向上尽量靠近

- 调用者和被调用者应该尽量地靠近。
- 概念相关的函数应该尽快靠近。

```java
public void start(){ 
    findJobStatus(); 
    retryIfNessary(); 
} 
private void findJobStatus() { } 
private void retryIfNessary() { }
```

```java
static public void assertTrue(boolean condition) { } 
static public void assertFalse(String message, boolean condition) { } static public void assertFalse(boolean condition) { }
```

#### 2.4 变量的申明尽量靠近变量的使用

- 本地变量应该尽量在使用前才申明；
- 成员变量、全局变量应该尽量放在源文件头部；

### 3. 水平格式

#### 3.1 每一行的宽度应该保证屏幕能显示全

- 建议每一行的宽度不超过120列。

#### 3.2 使用统一的换行和对齐规则

- 使用统一的代码风格模板，最好采用IDE的自动格式化功能；
- 提交代码前应该格式化代码；
- 调整代码风格标准后，重新格式化代码应该单独做一体提交；
- 不要留太多空行；

```java
public class FitNesseServer implements SocketServer { private FitNesseContext
context; public FitNesseServer(FitNesseContext context) { this.context =
context; } public void serve(Socket s) { serve(s, 10000); } public void
serve(Socket s, long requestTimeout) { try { FitNesseExpediter sender = new
FitNesseExpediter(s, context);
sender.setRequestParsingTimeLimit(requestTimeout); sender.start(); }
catch(Exception e) { e.printStackTrace(); } } }

-----


public class FitNesseServer implements SocketServer {
  private FitNesseContext context;


public FitNesseServer(FitNesseContext context) {
  this.context = context;
}

public void serve(Socket s) {
  serve(s, 10000);
}

public void serve(Socket s, long requestTimeout) {
  try {
    FitNesseExpediter sender = new FitNesseExpediter(s, context);
    sender.setRequestParsingTimeLimit(requestTimeout);
    sender.start();
  }
  catch (Exception e) {
    e.printStackTrace();
  }
}
}
```

## 六、错误处理

### 1. 异常优于错误代码

在很久以前，许多语言都不支持异常。你要么设置一个错误标识，要么返回给调用者检查的错误码。这类手段的问题在于，它们搞乱了调用者代码。调用者必须在调用之后即刻检查错误。不幸的是，这个步骤很容易被遗忘。

所以，遇到错误时，最好抛出一个异常。调用代码很整洁，其逻辑不会被错误处理搞乱。

```java
public class DeviceController {
  …

  public void sendShutDown() {
    try {
      tryToShutDown();
    } catch (DeviceShutDownError e) {
      logger.log(e);
    }
}

private void tryToShutDown() throws DeviceShutDownError {
  DeviceHandle handle = getHandle(DEV1);
  DeviceRecord record = retrieveDeviceRecord(handle);

  pauseDevice(handle);
  clearDeviceWorkQueue(handle);
  closeDevice(handle);
}

  private DeviceHandle getHandle(DeviceID id) {
  …
  throw new DeviceShutDownError(“Invalid handle for: ” + id.toString());
  …
}

…
}
```

### 2. 先写 Try-Catch-Finally 语句

在某种意义上，try 代码块就像是事务。先写出 try-catch-finally 语句能帮你定义代码的用户应该期待什么。

```java
@Test(expected = StorageException.class)
public void retrieveSectionShouldThrowOnInvalidFileName() {
  sectionStore.retrieveSection(“invalid - file”);
}
```

该测试驱动我们创建以下占位代码：

```java
public List<RecordedGrip> retrieveSection(String sectionName) {
  // dummy return until we have a real implementation
  return new ArrayList<RecordedGrip>();
}
```

测试失败了，因为以上代码并未抛出异常。下一步，修改实现代码，尝试访问非法文件。该操作抛出一个异常：

```java
public List<RecordedGrip> retrieveSection(String sectionName) {
  try {
    FileInputStream stream = new FileInputStream(sectionName)
  } catch (Exception e) {
    throw new StorageException(“retrieval error”, e);
  }
  return new ArrayList<RecordedGrip>();
}
```

这次测试通过了，因为我们捕获了异常。

### 3.  使用运行时异常

关于Runtime Exception和Checked Exception的辩论已结束，Runtime Exception胜出。

Checked Exception的代价就是违反开闭原则。

### 4. 给出异常发生的上下文环境说明

你抛出的每个异常，都应当提供足够的环境说明，以便判断错误的来源和处所。

应创建信息充分的错误消息，并和异常一起传递出去。在消息中，包括失败的操作和失败类型。如果你的应用程序有日志系统，传递足够的信息给 catch 块，并记录下来。

### 5. 根据异常处理者的需要来定义异常类型

对错误分类有很多方式。当我们在应用程序中定义异常类时，最重要的考虑应该是它们如何被处理。

来看一个不太好的异常分类例子。

```java
ACMEPort port = new ACMEPort(12);

try {
  port.open();
} catch (DeviceResponseException e) {
  reportPortError(e);
  logger.log(“Device response exception”, e);
} catch (ATM1212UnlockedException e) {
  reportPortError(e);
  logger.log(“Unlock exception”, e);
} catch (GMXError e) {
  reportPortError(e);
  logger.log(“Device response exception”);
} finally {
  …
}
```

既然知道我们所做的事不外如此，就可以通过打包调用 API、确保它返回通用异常类型，从而简化代码。

```java
LocalPort port = new LocalPort(12);
try {
  port.open();
} catch (PortDeviceFailure e) {
  reportError(e);
  logger.log(e.getMessage(), e);
} finally {
  …
}
```

### 6. 将异常场景转换为正常场景

以下是一段计算餐费的代码，如果餐费发生则按照实际发生金额计算入账单，如果没有则按照固定报销额度计入账单。

```java
try {
  MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
  m_total += expenses.getTotal();
} catch(MealExpensesNotFound e) {
  m_total += getMealPerDiem();
}
```

如果改造ExpenseReportDAO，让其在没有餐费时返回一种特殊的餐费类型，该类型的餐费就是报销金额，这样就不需要有异常处理的逻辑了。

```java
public class PerDiemMealExpenses implements MealExpenses {
public int getTotal() {
// return the per diem default
 }
}

MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
m_total += expenses.getTotal();

```

这种手法叫做特例模式（SPECIAL CASE PATTERN，[Fowler]）。创建一个类或配置一个对象，用来处理特例。你来处理特例，客户代码就不用应付异常行为了。异常行为被封装到特例对象中。

### 7. 不要返回 null 值

使用Special Case Pattern应对可能为Null的场景，减少Null Defence的代码，简化代码结构。
```java
List<Employee> employees = getEmployees();
if (employees != null) {
  for(Employee e : employees) {
    totalPay += e.getPay();
  }
}
```
V.S

```java
List<Employee> employees = getEmployees();
for(Employee e : employees) {
  totalPay += e.getPay();
}
```

```java
public List<Employee> getEmployees() {
  if( .. there are no employees .. )
    return Collections.emptyList();
}
```

### 8. 别传递 null 值

在方法中返回 null 值是糟糕的做法，但将 null 值传递给其他方法就更糟糕了。

举例说明原因。用下面这个简单的方法计算两点的投射：

```java
public class MetricsCalculator
{
  public double xProjection(Point p1, Point p2) {
    return (p2.x – p1.x) * 1.5;
  }
  …
}
```

如果有人传入 null 值会怎样？

```java
calculator.xProjection(null, new Point(12, 13));
```

如何修正？可以创建一个新异常类型并抛出：

```java
public class MetricsCalculator
{
public double xProjection(Point p1, Point p2) {
  if (p1 == null || p2 == null) {
      throw InvalidArgumentException(
        “Invalid argument for MetricsCalculator.xProjection”);
  }
  return (p2.x – p1.x) * 1.5;
}
}
```

这样可能比 null 指针异常好一些。

可以使用一组断言

```java
public class MetricsCalculator
{
  public double xProjection(Point p1, Point p2) {
    assert p1 != null : “p1 should not be null”;
    assert p2 != null : “p2 should not be null”;
    return (p2.x – p1.x) * 1.5;
  }
}
```

看上去很美，但仍未解决问题。如果有人传入 null 值，还是会得到运行时错误。

### 9. 错误处理小结

整洁代码是可读的，但也要强壮。如果将错误处理隔离看待，独立于主要逻辑之外，就能写出强壮而整洁的代码。



## 七、单元测试

### 1. 整洁测试的重要性

- 肮脏的单元测试，比没有单元测试更糟糕

如果单元测试本身难以维护，它就会变成开发团队的额外负担，测试无法体现其功能，最终不得不抛弃测试。

- 单元测试保证代码拥有各种能力

没有整洁的单元测试，你就无法进行有效的重构，从而导致业务代码就会逐渐丧失灵活性、可维护性和可读性。

### 2. 整洁测试

- **可读性是整洁测试的基本精神**

1.    首先，测试要有良好的命名。

   建议使用Given-When-Then模式来为单元测试命名：

   Given：描述测试的输入或者测试场景

   When：描述被测功能

   Then： 描述期望结果

   例子:

```java
public void testCreateUnit_Given_duplicate_Request_Expect_Request_Waiting_In_Queue() throws Exception{
}
```

2.   其次，每一个单元测试只能有一个断言。

   在一个单元测试中只能测试一个概念，一个测试只有一个失败的原因。

3.   最后，测试代码也需要有良好的结构

   测试内部代码应该符合Setup-Action-Check模式：

​    **Setup**: 准备测试数据，设置mock等

​    **Action**: 执行测试方法

​    **Check**: 验证测试结果

   代码：

```java
@Test
public void testCreateUnit_Given_Legal_Request_Body_Expect_Dispatch_Response() throws Exception {
    String key = RandomUtils.getUUIDWithoutDash();
    String json = TestUtils.loadResourceAsString("test_data/unit.json");
    DispatchResponse response = baseTarget
                                   .path(key)
                                   .request()
                                   .accept(MediaType.APPLICATION_JSON)
                                   .post(Entity.json(json), DispatchResponse.class);
    assertEquals(0, response.getStatus());
    verify(kafkaService, times(1)).send(any(DispatchMessage.class));
}
```

- **整洁的单元测试需要符合F.I.R.S.T原则**

1. **Fast** **：**测试执行必须快;
2. **Independent** ：测试之间不需互不依赖;
3. **Repeatable** ：测试可以在任何环境下重复执行;
4. **Self-Validating** **：**测试必须是可自我验证的，不需要人工干预;
5. **Timely**: 测试必须及时写，至少在产品发布之前应该写完测试;