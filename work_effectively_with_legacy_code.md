# 如何维护遗留代码

## 1. 什么是遗留代码?

通常认为难以理解和维护的代码就是遗留代码。

我们通常给遗留代码一些昵称：烂代码、大泥球、一团糟...

> 遗留代码就是没有测试的代码。--Michael Feathers

不管代码写得多好，只要没有测试，我们就认为这种代码是很差的代码。

因为没有测试就意味着：

- 代码结构很差，没有可测性，因而无法测试；
- 难以理解当前代码的功能，没有机制保证可以继续添加新功能；
- 难以在不破坏现有功能的前提下进行优化和改进，无法遏制腐化的趋势；

## 2. 如何应对遗留代码?

### 2.1 理解遗留代码的历史

“冰冻三尺，非一日之寒!" 烂代码也不是一天造成的！反思造成当前状态的原因有助于避免我们重复同样的错误。

一些常见的原因：

- 过分追求“稳定”的团队文化：“只要不出问题，就不要动代码！”
- 进度第一，质量第二：“不管你们用什么方法，明天要按时上线！”
- 忽视技术债务：“等我有空了，我就会重构系统！”
- 缺乏写好代码的技能：“从来没有人告诉我要如何写好代码！”
- ....

### 2.2 改善现状的方法

#### 2.2.1 团队改进

在我们尝试改进系统之前，第一要务是改进团队的工作方式。软件系统的腐坏的根源往往在于开发团队本身，为团队树立正确的价值观和文化，培养团队的技能，才是根本解决之道。

#####  1） 团队：

- 与熟悉系统历史的团队人员一起工作，确定团队和系统需要改进的方向。
- 选择典型功能进行重构，为系统改进方向树立典型样板和模式。
- 在团队中传播典型样板和模式，让团队具备必要信息和技能。
- 和团队达成改进的承诺。

#####  2）计划：

- 确定需要解决的系统问题。
- 制定系统改进计划，将改进任务加入迭代。
- 在每一个迭代中持续进行改进。

##### 3） 工具与流程

使用静态代码扫描工具让代码换乱可视化，持续进行整改。

> 童子军法则：离开营地时总是让营地比你到来是干净！

#### 2.2.2  系统改进

##### 1） 关键是可读性

整洁代码不但关于效率，有些时候决定了系统的生死存亡！

##### 2）设计模式

学习、应用和分享设计模式。如果团队成员都能理解设计模式，那么团队将能写出灵活且易读的代码。

##### 3）测试

关注团队使用的测试金字塔模型，让测试方案和计划透明，大部分团队的测试都存在改进空间。

##### 4）架构

软件架构的一个目标就是让软件能够适应将来的变化，既要有前瞻性，又要避免过度复杂。

## 3. 修改代码的艺术

### 3.1 修改代码的原因有哪些?

1. 增加特性：在保持当前系统功能不变的情况下，增加新的功能；
2. 修复缺陷：保持其他行为不变的情况下，修复某些行为的缺陷；
3. 改进设计：保持代码外部行为不变的前提下，改进代码设计；
4. 优化资源使用：保持代码外部行为不变的前提下，调整代码以提升资源使用；

修改代码前最重要的是搞清楚修改对于现有系统功能的影响。

### 3.2 遗留代码的困境

当我们修改代码时，我们应该先写测试。要写测试，我们必须先修改代码。

### 3.3 修改遗留代码的步骤

1. 确定变更点
   变更点取决于架构，只有对设计足够了解，才能确定在正确的地方做出变更。

2. 确定测试方法
   我们需要决定在哪里为特定的变更编写测试。

3. 打破依赖
   依赖是测试最大的阻碍，只有打破依赖才能进行测试。

4. 编写写测试

5. 修改代码并进行重构

### 3.4 如何确保不破坏系统现有功能

#### 3.4.1  规则

1. 超感编辑
   超感编辑就是准确地知道每次敲击键盘时都知道在做什么。结对编程和TDD能让我们达到超感编辑的状态。

2. 单一目标编辑
   作为程序员，我们应该时刻提醒自己“编程是每次只做一件事的技术”。当我们结对时，总是会让搭档帮忙确认，“你在做什么？”如果答案超过一件事，那么就从中选择一件。

3. 保留签名
   为了编写测试，我们需要打破依赖，此时要尽可能保留方法签名，这样能最大程度上避免出错。

4. 依赖工具
   编译器、IDE等工具能够帮助我们自动完成错误检查、重构，提升效率的同时减少了错误。

5. 结对编程
   结对编程对于提升质量和知识传播是非常好的方式。

#### 3.4.2  接缝

接缝就是可以变更程序行为但又用不着修改当前程序的地方。

对象接缝是面向对象的程序设计语言中提供的最有用的接缝。针对被测试代码，其调用的对象就是对象接缝，因为我们可以很容易地将这种对象替换为伪协作程序，而不用修改被测试代码本身。

#### 3.4.3 特性测试

在修改遗留代码的过程中，自动化测试是用来保证已有的功能不被改变，或者说提供了一种安全网。

在写测试之前，我们先要搞清楚系统到底有哪些功能。在遗留系统中，通过需求文档搞清楚这个问题往往不是好的方式，因为系统当前的功能和对系统的功能期望可能是两回事。

所谓特性测试就是针对一小块代码当前的行为进行的测试。其基本步骤为：

1. 针对一小片代码进行测试；
2. 写一些你觉得会失败的断言；
3. 让测试失败告诉你真正的系统行为；
4. 修改测试，迎合当前的系统行为；
5. 重复

举例，下面例子中，我们尝试测试案例为：

```java
void testGenerator() {
    PageGenerator generator = new PageGenerator();
    assertEquals("", generator.generate());
}
```

测试通过了。

这个测试记录了PageGenerator当前功能的一种基本事实。

现在，我们假设PageGenerator会输出字符串“fred”:

```java
void testGenerator() {
        PageGenerator generator = new PageGenerator();
        assertEquals("fred", generator.generate());
    }
}
```

测试失败，错误信息为:

```java
Time: 0.01
There was 1 failure:
    1) testGenerator(PageGeneratorTest)
junit.framework.ComparisonFailure: expected:<fred> but was:<<node><carry>1.1 vectrai</carry></node>>
at PageGeneratorTest.testGenerator
    (PageGeneratorTest.java:9)
at sun.reflect.NativeMethodAccessorImpl.invoke0
    (Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke
    (NativeMethodAccessorImpl.java:39)
at sun.reflect.DelegatingMethodAccessorImpl.invoke
    (DelegatingMethodAccessorImpl.java:25
```

因此， 我们现在可以修改测试案例为：

```java
void testGenerator() {
        PageGenerator generator = new PageGenerator();
        assertEquals("<node><carry>1.1 vectrai</carry></node>", generator.generate());
    }
}
```

如果你习惯于把测试仅仅当做测试，则上述代码看起来会非常怪异。但是，如果你把这种测试当成固定当前系统行为的工具，则它就可以确保我们不破坏当前系统行为。

#### 3.4.4  拦截点

- 拦截点是在程序中可以检测当前变更结果的位置。越靠近变更点的拦截点越好。

#### 3.4.5 流程

- 寻找接缝，如果没有则使用自动化重构工具制造基本的接缝。
- 打破依赖，依赖于抽象而不是具体。
- 创建特性测试作为安全网。
- 针对修改的功能构建测试，使用测试替身代替依赖，针对拦截点进行验证。
- 做出代码修改，进行测试验证和重构。

### 4.  打破依赖

#### 4.1 感知和分离

理想情况下，我们可以立即创建测试，然后开始修改了。但是，现实情况往往很糟糕：我们需要打破错综复杂的依赖关系才能编写单元测试；我们需要被测试的类对其他类的影响，因为测试需要这些信息。

一般说来，当我们想让测试就位时，我们就有两种理由可以打破依赖：

1. 感知：我们无法获得代码的计算结果。
2. 分离：我们无法将一小块代码放到测试中调用。

感知与分离哪个更难解决呢？我们没有答案。通常，两个问题都需要解决。

#### 4.2 测试替身

在面向对象的程序中，我们可以使用一个测试替身来打破依赖，从而使测试可以进行。

典型的如：

- Dummy
   作为填充参数的占位符，测试过程中不会有实际的使用。

- Fake
   虚假的实现，可以工作，但不是按照真实的方式工作。
- Stub
   在测试过程中，无论何种调用都只返回预设的固定答案。

- Spy
   被监控了的对象，除了执行真实操作外还偷偷执行间谍行为。

- Mock
   根据预设规则返回不同响应的虚假实现。

#### 4.3 打破依赖的原则

为了让代码变得更好，我们有时候需要让代码的某些方面变得更糟。

Testable & Clear > **Testable & Muddy** > **Untestable & Clear** > Untestable & Muddy

在遗留代码中打破依赖时，我们常常需要暂时放弃我们代码洁癖。这就好比动手术总会留下伤疤，但是伤疤之下通常比动手术之前要好。

##### 4.3.1 平衡不同修改的优先级同样很重要

- 新功能优先？
- 设计改进优先？
- 测试优先？

### 5. 打破依赖的代码实践

#### 5.1 参数化构造方法

**定义：**

将构造方法中直接创建依赖对象，修改为通过参数传入依赖对象。

**代码示例：**

```java
public class MailChecker
{
    public MailChecker (int checkPeriodSeconds) {
        this.receiver = new MailReceiver();
        this.checkPeriodSeconds = checkPeriodSeconds;
    }
  ...
}
```

MailChecker在构造方法中直接构造了MailReceiver的对象，从而造成了强依赖。

```java
public class MailChecker
{
    public MailChecker (int checkPeriodSeconds) {
        this(new MailReceiver(), checkPeriodSeconds);
    }
    public MailChecker (MailReceiver receiver,
                        int checkPeriodSeconds) {
        this.receiver = receiver;
        this.checkPeriodSeconds = checkPeriodSeconds;
    }
  ...
}
```

采用参数化构造方法，我们保留了原有构造方法的签名，增加了打破依赖的新构造方法。

#### 5.2 参数化方法

**定义：**

当一个方法在其内部构造了一个依赖对象，我们需要分离这个依赖，或者通过这个依赖感知测试结果时，我们可以将这个依赖提取成为方法的参数。

**代码示例**：

```java
public void printBooks(List<Book> books) {
    PrintWriter printWriter = new PrintWriter(System.out);
    for (Book book : books) {
        printWriter.println(book.getName());
    }
}
```

上述代码在测试过程中无法直接感知标准输出的输出结果，为了打破依赖，我们可以参数化方法：

```java
public void printBooks(List<Book> books) {
    this.printBooks(books,new PrintWriter(System.out));
}

public void printBooks(List<Book> books,PrintWriter printWriter) {
    for (Book book : books) {
        printWriter.println(book.getName());
    }
}
```

####  5.3 新生方法

**定义：**

向系统添加功能时，可以通过添加新方法，然后在功能需要的地方进行调用的方式。

**代码示例：**

例如，下面代码：

```java
public class TransactionGate {
    public void postEntries(List entries) {
        for (Entry entry:entries ) {
            entry.postDate();
        }
        transactionBundle.getListManager().add(entries);
    }
    //more code
}
```

现在，我们需要修改代码保证日期在添加之前不存在于transactionBundle中。

```java
public class TransactionGate {
    public void postEntries(List entries) {
        List entriesToAdd = new LinkedList();
        for (Entry entry:entries) {
            if (!transactionBundle.getListManager().hasEntry(entry) {
                entry.postDate();
                entriesToAdd.add(entry);
            }
        }
        transactionBundle.getListManager().add(entriesToAdd);
    }
    //more code
}
```

这种修改是具有侵略性的，因为新添加的代码和旧代码之间没有进行分离。更糟糕的是，我们无法单独验证新添加的功能是否正确。

我们可以换一种修改方式，添加新方法，在原有代码中调用新方法：

```java
public class TransactionGate {
   List uniqueEntries(List entries) {
        List result = new ArrayList();
        for (Entry entry:entries ) {
            if (!transactionBundle.getListManager().hasEntry(entry){
                result.add(entry);
            }
        }
        return result;
    }

    public void postEntries(List entries) {
        List entriesToAdd = uniqueEntries(entries);
        for (Entry entry:entries) {
            entry.postDate();
        }
        transactionBundle.getListManager().add(entriesToAdd);
    }
    //more code
}
```

####  5.4 新生类

**定义：**

向系统添加功能时，可以通过添加新类，然后在功能需要的地方调用新类。

**代码示例：**

假设我们有如下功能：

```java
public class QuarterlyReportGenerator {
    //a lot of code here
   public String generate() {
     List<Result> results = database.queryResults(beginDate, endDate);
     String pageText = "<html><head><title>Quarterly Report</title></head><body><table>";
     if (results.size() != 0) {
            for (Result result : results) {
                pageText += "<tr>";
                pageText += "<td>" + it -> department + "</td>";
                pageText += "<td>" + it -> manager + "</td>";
                pageText += "<td>" + (result.getNetProfit() / 100) + "</td>";
                pageText += "<td>" + (result.getOperatingExpense() / 100) + "</td>";
                pageText += "</tr>";
            }
      } else {
            pageText += "No results for this period";
      }
      pageText += "</table></body></html>";
      return pageText;
    }
    //a lot of code here
}
```

现在我们要为生成的HTML表格添加一个表头：

```html
<tr><td>Department</td><td>Manager</td><td>Profit</td><td>Expenses</td></tr>
```

我们再假设当前这个类很大，要给这个类添加测试要花一天，而目前我们来不及这么做。

所以，我们可以为这次变更生成一个新的类，并且采用TDD的方式来开发：

```java
class QuarterlyReportTableHeaderProducer {
    public String makeHeader() {
        return "<tr><td>Department</td><td>Manager</td><td>Profit</td><td>Expenses</td>”;
    }
}
public class QuarterlyReportGenerator {
    private QuarterlyReportTableHeaderProducer headerProducer;
    //a lot of code here
    public String generate() {
     List<Result> results = database.queryResults(beginDate, endDate);
     String pageText = "<html><head><title>Quarterly Report</title></head><body><table>";
     pageText += headerProducer.makeHeader();
     if (results.size() != 0) {
            for (Result result : results) {
                pageText += "<tr>";
                pageText += "<td>" + it -> department + "</td>";
                pageText += "<td>" + it -> manager + "</td>";
                pageText += "<td>" + (result.getNetProfit() / 100) + "</td>";
                pageText += "<td>" + (result.getOperatingExpense() / 100) + "</td>";
                pageText += "</tr>";
            }
        } else {
            pageText += "No results for this period";
        }
        pageText += "</table></body></html>";
        return pageText;
    }
    //a lot of code here
}
```

你可以可能觉得有点夸张，为了这样一行代码居然要新增加一个类。但是，这正是我们应对当前类依赖复杂，难以测试的修改方式。

#### 5.5 分解方法对象

**定义：**

当方法很长，且使用本地变量和方法，则可以将方法提取为独立的对象。

**代码示例：**

```java
public class Order {
    private List<OrderLineItem> OrderLineItems;
    private List<Double> Discounts;
    private Double Tax;
    
    public Order(Tax tax, Disconount disount ...){
        //a lot of code here
    }

    public Double Calculate() {
        Double subTotal = 0d;
        // Total up line items 
        for (OrderLineItem lineItem : OrderLineItems) {
            subTotal += lineItem.Price;
        }
        // Subtract Discounts 
        for (Double discount : Discounts) subTotal -= discount;
        // Calculate Tax 
        Double tax = subTotal * Tax;
        // Calculate GrandTotal 
        Double grandTotal = subTotal + tax;
        return grandTotal;
    }
    //a lot of other code
}
```

上述Order类的Calculate方法很复杂，除此以外，其构造过程很复杂，且还有其他很多方法。如果我们想修改Calculate并且只针对我们要修改的部分进行测试，我们就可以考虑分解方法对象。

```java
public class Order {
    public List<OrderLineItem> OrderLineItems;
    public List<Double> Discounts;
    public Double Tax;

    public Double Calculate() {
        return new OrderCalculator(this).Calculate();
    }
}

public class OrderCalculator {
    private Double SubTotal;
    private List<OrderLineItem> OrderLineItems;
    private List<Double> Discounts;
    private Double Tax;

    public OrderCalculator(Order order) {
        OrderLineItems = order.OrderLineItems;
        Discounts = order.Discounts;
        Tax = order.Tax;
    }

    public Double Calculate() {
        CalculateSubTotal();
        SubtractDiscounts();
        CalculateTax();
        return SubTotal;
    }

    private void CalculateSubTotal() {
        for (OrderLineItem lineItem : OrderLineItems) SubTotal += lineItem.Price;
    }

    private void SubtractDiscounts() {
        for (Double discount : Discounts) SubTotal -= discount;
    }

    private void CalculateTax() {
        SubTotal += SubTotal * Tax;
    }
}
```

#### 5.6 提取并重写方法调用

**定义**

如果在测试过程中阻碍我们的依赖都是局部方法调用的，可以通过继承并重写局部方法来打破依赖。

**代码示例**

```java
public class PageLayout
{
    private int id = 0;
    private List styles;
    private StyleTemplate template;
    ...
    protected void rebindStyles() {
        styles = StyleMaster.formStyles(template, id);
        ...
    }
    ...
}
```

PageLayout调用了StyleMaster类上名为formStyle的静态函数。如果我们要分离对于StyleMaster的依赖，那么能做什么呢？

```java
    public class PageLayout
    {
        private int id = 0;
        private List styles;
        private StyleTemplate template;
        ...
        protected void rebindStyles() {
            styles = formStyles(template, id);
            ...
        }
        protected List formStyles(StyleTemplate template, int id) {
            return StyleMaster.formStyles(template, id);
        }
        ...
    }
    public class TestingPageLayout extends PageLayout {
        protected List formStyles(StyleTemplate template, int id) {
            return new ArrayList();
        }
        ...
    }
```

当我们需要多种样式的测试时，我么可以修改这个方式，从而配置返回什么。

#### 5.7 提取并重写工厂方法

**定义：**

在构造函数中直接创建依赖对象时，我们提取依赖对象创建过程为工厂方法，在子类中覆盖工厂方法以打破依赖。

**代码示例：**

```java
public class WorkflowEngine {
    public WorkflowEngine() {
        Reader reader= new ModelReader(AppConfig.getDryConfiguration());
        Persister persister= new XMLStore(AppConfiguration.getDryConfiguration());
        this.tm = new TransactionManager(reader, persister);
        ...
    }
    ...
}
```

我们可以提取一个工厂方法，并且在子类中进行重写。

```java
public class WorkflowEngine {
    public WorkflowEngine() {
        this.tm = makeTransactionManager();
        ...
    }

    protected TransactionManager makeTransactionManager() {
        Reader reader = new ModelReader(AppConfiguration.getDryConfiguration());
        Persister persister = new XMLStore(AppConfiguration.getDryConfiguration());
        return new TransactionManager(reader, persister);
    }
    ...
}
public class TestWorkflowEngine extends WorkflowEngine{
        protected TransactionManager makeTransactionManager() {
            return new FakeTransactionManager();
        }
    }
```

#### 5.8 上移特性

**定义：**

将你想要测试的功能上移到抽象类中，测试这个抽象类的子类。

**代码示例：**

```java
public class Scheduler {
    private List items;

    public void updateScheduleItem(ScheduleItem item) throws SchedulingException {
        try {
            validate(item);
        } catch (ConflictException e) {
            throw new SchedulingException(e);
        }
        ...
    }

    private void validate(ScheduleItem item) throws ConflictException {
        // make calls to a database
       ...
    }

    public int getDeadtime() {
        int result = 0;
        for (Iterator it = items.iterator(); it.hasNext(); ) {
            ScheduleItem item = (ScheduleItem) it.next();
            if (item.getType() != ScheduleItem.TRANSIENT && notShared(item)) {
                result += item.getSetupTime() + clockTime();
            }
            if (item.getType() != ScheduleItem.TRANSIENT) {
                result += item.finishingTime();
            } else {
                result += getStandardFinish(item);
            }
        }
        return result;
    }
}
```

在上例中，我们需要修改Scheduler的getDeadtime()的功能。但是由于Scheduler还依赖于数据库，即使getDeadtime()与数据库无关，我们仍然存在对于数据库的依赖。

```java
public abstract class SchedulingServices {
    protected List items;

    protected boolean notShared(ScheduleItem item) {
    ...
    }

    protected int getClockTime() {
     ...
    }

    protected int getStandardFinish(ScheduleItem item) {
     ...
    }

    public int getDeadtime() {
        int result = 0;
        for (Iterator it = items.iterator(); it.hasNext(); ) {
            ScheduleItem item = (ScheduleItem) it.next();
            if (item.getType() != ScheduleItem.TRANSIENT&& notShared(item)) {
                result += item.getSetupTime() + clockTime();
            }
            if (item.getType() != ScheduleItem.TRANSIENT) {
                result += item.finishingTime();
            } else {
                result += getStandardFinish(item);
            }
        }
        return result;
    }
    ...
}
public class Scheduler extends SchedulingServices
{
    public void updateScheduleItem(ScheduleItem item) throws SchedulingException {
          ...
    }
    private void validate(ScheduleItem item) throws ConflictException {
    // make calls to the database
         ...
    }
    ...
}
public class TestingSchedulingServices extends SchedulingServices
{
  public TestingSchedulingServices() {
  }
  public void addItem(ScheduleItem item) {
    items.add(item);
  }
}
```

我们将getDeadtime()上移到抽象类中，在测试阶段就可以覆盖与getDeadtime()无关的其他方法，从而打破与本次变更无关的依赖。

#### 5.9 下沉依赖

**定义：**

将当前的被测试类变为抽象类，将依赖下沉到其子类中，为抽象类创建测试子类用于测试。

**代码示例：**

```java
public class Monster {
    private Physics physics = Physics.getInstance();
    private Rendering rendering = new Rendering();

    private Integer hitPoints;
    private String state;
    private Vector2 position;
    private Integer damage = 2;
    // many more instance variables


    public Monster(Integer hitPoints, String state, Vector2 position) {
        this.hitPoints = hitPoints;
        this.state = state;
        this.position = position;
        // Push Physics and Rendering down
        physics.add(this);
        rendering.render(this);
    }

    public void processAi() {
        if (hitPoints > 5) {
            Monster nearestEnemy = findNearestEnemy();
            if (state.equals("Angry")) {
                moveTo(nearestEnemy);
                attack(nearestEnemy);
            } else if (state.equals("Afraid")) {
                moveAwayFrom(nearestEnemy);
            }
        } else {
            rest();
        }
    }

    public Monster findNearestEnemy() {
        return physics.findNearestEntityTo(position);
    }
    
    public void draw() {
        rendering.render(this);
    }

    public void moveTo(Vector2 position) {
        this.position = position;
        physics.move(this, position);
    }

    public void rest() {
       ...
    }

    public void moveAwayFrom(Monster target) {
       ...
    }

    public void attack(Monster target) {
       ...
    }

    public void moveTo(Monster target) {
       ...
    }
   
}
```

上例中，Physics和Rendering都与物理硬件有关，在测试阶段形成了依赖。因此，考虑将依赖部分下沉到子类。

```java
public  class Monster {
    ...

    public Monster(Integer hitPoints, String state, Vector2 position) {
        this.hitPoints = hitPoints;
        this.state = state;
        this.position = position;
    }

    public void processAi() {
        if (hitPoints > 5) {
            Monster nearestEnemy = findNearestEnemy();
            if (state.equals("Angry")) {
                moveTo(nearestEnemy);
                attack(nearestEnemy);
            } else if (state.equals("Afraid")) {
                moveAwayFrom(nearestEnemy);
            }
        } else {
            rest();
        }
    }

    protected Monster findNearestEnemy(){};
    protected  void draw(){};
    protected void moveTo(Vector2 position) {};
}

public class ConcreteMonster extends AbstractMonster {
    // Push Physics and Rendering down
    private Physics physics = Physics.getInstance();
    private Rendering rendering = new Rendering();

    public ConcreteMonster(Integer hitPoints, String state, Vector2 position) {
        super(hitPoints, state, position);
        physics.add(this);
        rendering.render(this);
    }
    @Override
    public Monster findNearestEnemy() {
        return physics.findNearestEntityTo(this.getPosition());
    }
    @Override
    public void draw() {
        rendering.render(this);
    }
    @Override
    public void moveTo(Vector2 position) {
        this.position = position;
        physics.move(this, position);
    }
}
```

这样，针对Monster的测试就不再依赖于硬件了。

#### 5.10提取静态方法

**定义：**

如果方法不依赖于于类的实例数据和方法，则可以将方法变成静态的，从而打破对于实例对象的依赖。

**代码示例：**

```java
class RSCWorkflow
{
    ...
    public void validate(Packet packet) throws InvalidFlowException {
        if (packet.getOriginator().equals( "MIA")
                || packet.getLength() > MAX_LENGTH
                || !packet.hasValidCheckSum()) {
            throw new InvalidFlowException();
        } 
     ...
    }
    ...
}
```

因为validate()方法与RSCWorkflow的实例变量和方法无关，因此可以提取为静态方法。

```java
public class RSCWorkflow {
    public void validate(Packet packet) throws InvalidFlowException {
        validatePacket(packet);
    }
    public static void validatePacket(Packet packet)throws InvalidFlowException {
        if (packet.getOriginator() == "MIA"
                || packet.getLength() <= MAX_LENGTH
                || packet.hasValidCheckSum()) {
            throw new InvalidFlowException();
        }
     ...
    }
  ...
}
```

提取静态方法后，测试可以直接针对静态方法，从而打破了对于对象的依赖。

####  5.11 包装方法

**定义：**

引入一个新的方法，这个方法调用新增功能的方法和原有方法。

**代码示例：**

在下面方法中，我们为员工增加了每日考勤，然后把他的工资信息发送给PayDispatcher。

```java
public class Employee {
    //a lot of code here
    public void pay() {
        Money amount = new Money();
        for (Timecard card : timecards) {
            if (payPeriod.contains(date)) {
                amount.add(card.getHours() * payRate);
            }
        }
        payDispatcher.pay(this, date, amount);
    }
}
```

现在假设我们有一个新需求，在发起支付之前我们需要先更新支付日志文件。我可以把原来的pay()方法改名为私有的dispatchPayment()方法，新建一个pay()方法调用记录支付日志的方法和原来的dispatchPayment()方法。

```java
public class Employee {
    private void dispatchPayment() {
        Money amount = new Money();
        for (Timecard card : timecards) {
            if (payPeriod.contains(date)) {
                amount.add(card.getHours() * payRate);
            }
        }
        payDispatcher.pay(this, date, amount);
    }

    public void pay() {
        logPayment();
        dispatchPayment();
    }

    private void logPayment() {
        //a lot of code here
    }
}
```

当然，如果支付之前记录日志并不是所有流程必须的，那么我们也可以在不改变原有方法命名的情况下新增包装方法。例如：

```java
public class Employee
{
    public void makeLoggedPayment() {
        logPayment();
        pay();
    }
    public void pay() {
    ...
    }
    private void logPayment() {
    ...
    }
}
```

#### 5.12 包装类

**定义：**

引入一个新的类，这个类的方法中调用新增功能的方法和原有方法，是装饰者模式的应用。

**代码示例：**

```java
class Employee
{
    public void pay() {
        Money amount = new Money();
        for (Timecard card： timecards) {
            if (payPeriod.contains(date)) {
                amount.add(card.getHours() * payRate);
            }
        }
        payDispatcher.pay(this, date, amount);
    }
    ...
}
```

我们想要为特定员工的支付记录日志，所以可以增加一个拥有pay方法的类，让这个类拥有Employee的实例，在pay方法中完成日志记录同时调用employee完成支付操作。

```java
class LoggingEmployee extends Employee {
    public LoggingEmployee(Employee e) {
        employee = e;
    }

    public void pay() {
        logPayment();
        employee.pay();
    }

    private void logPayment() {
     ...
    }
     ...
}
```

#### 5.13 适配参数

**定义：**

测试函数时，函数参数难以构造，且无法提取接口，则可以使用适配器打破依赖。

**代码示例：**

```java
public class ARMDispatcher
{
    public void populate(HttpServletRequest request) {
        String [] values= request.getParameterValues(pageStateName);
        if (values != null && values.length > 0)
        {
            marketBindings.put(pageStateName + getDateStamp(),values[0]);
        }
    ...
    }
    ...
}
```

参数HttpServletRequest已经是接口，且无法很容易的构造一个实现，因而成为测试的障碍。

```java
class ServletParameterSource implements ParameterSource
    {
        private HttpServletRequest request;
        public ServletParameterSource(HttpServletRequest request) {
            this.request = request;
        }
        String getParameterValue(String name) {
            String [] values = request.getParameterValues(name);
            if (values == null || values.length < 1)
                return null;
            return values[0];
        }
 }
 
public class ARMDispatcher {
public void populate(ParameterSource source) {
    String values = source.getParameterForName(pageStateName);
    if (value != null) {
        marketBindings.put(pageStateName + getDateStamp(), value);
    }
    ...
}
```

我们通过将HttpServletRequest适配为ParameterSource接口，就可以将依赖变得更加容易实例化，从而打破依赖。

```java
class FakeParameterSource implements ParameterSource {
        public String value;
        public String getParameterForName(String name) {
            return value;
        }
}
```

####  5.14 封装全局引用

**定义：**

如果全局变量成为依赖，将全局变量包裹在一个类中，使用getter来获取全局变量。

**代码示例：**

暂无

#### 5.15 封装全局静态方法

**定义：**

如果全局静态方法称为依赖，将全局静态方法包裹在一个类中，通过类的实例方法来访问。

**代码示例：**

暂无

#### 5.16 原始化参数

**定义**：

如果方法的参数难以构造，而被测方式只需要参数的部分原始字段，则可以将参数列表修改为直接使用原始字段。

注意：此举会打破封装，但也是一种变通的方法。

**代码示例：**

```java
public Vector findMidpoint(Monster monster1, Monster monster2) {
    return monster1.position().average(monster2.position());
}
```

上例中，如果Monster很难构造，因为findMidpoint其实只需要Position，所以可以原始化参数为：

```java
private Vector findMidpoint(Position position1, Position position2) {
    return position1.average(position2);
}
```

### 6. 通用实践

#### 6.1 理解性重构

重构是理解代码的最佳技术之一。没有测试的重构是有很风险的操作，但是只要不提交代码，就不会造成破坏性。你可以按照重构的方式提取方法、移动代码、重命名变量，等到你充分理解代码以后回滚所有变更。

理解性重构存在以下风险：

第一，如果重构时我们犯一些严重错误，会导致我们误解系统的功能。

第二，我们可能太过沉迷于重构本身，而忽略更好结构和不同的看法。

#### 6.2 使用自动化重构工具

在没有测试的情况下做自动化重构，需要自动化重构工具的支持，以便安全地做很多低级的工作。

使用自动化重构工具提取小函数，以便：

1. 从不合适的依赖中分离出逻辑；
2. 引入接缝，是编写测试更加容易，从而进行更多的重构；

### 7. 常见的困境

#### 7.1 时间很紧张，但还需要修改

让我们面对现实，在时间很紧张的情况下，我们无法为遗留代码补充测试，也无法拒绝修改。但是，我们可以利用“包装类”、“包装方法”、“新生类”、“新生方法”的方式为新代码写单元测试，同时和遗留代码保持距离。

这是一种无奈的选择，因为遗留代码没有得到任何改善。但是在写有测试的新代码的过程中，我们培育了团队，也为长期的重构进行了铺垫。

#### 7.2 永远都无法完成的修改

有时候代码实在太烂了，修改代码看起来永远都无法完成。此时，我们采取的策略不应该是更加“努力”地修改，而是考虑：

**增强理解：**将系统分解为小型、命名良好、易于理解的小部分。
**构建反馈：**构建反馈机制，减少从你做出代码修改到获得变更对系统影响的花费的时间。
**打破依赖：**打破它的依赖关系，从而可以单独测试要修改的功能。

#### 7.3 我要修改代码，应该测试哪些地方？

最直接的想法就是，当前代码影响了那些代码，就针对这些代码进行测试。不过，在特别复杂的遗留代码中，找出影响的范围并不容易。
一些措施是：
**绘制影响草图推断影响：**
简单地用一个圆圈代表功能，用箭头指向受影响的功能，成为影响草图。如果我们将各个部分的影响操作组合在一起，我们就得到了影响的范围。
**通过IDE和编译器的帮助来推断影响：**
1. 确定要变更的方法；
2. 如果方法有返回值，那么就查看调用它的程序；
3. 如果方法会修改某些值，那么就查看使用这些值得方法，以及使用这些方法的方法；
4. 确保查看了可能使用这些实例变量的超类和子类；
5. 查看传递给方法的参数，看它自己活着它的方法返回的对象是否被要修改的代码使用；
6. 查找你确定的任何一个方法中修改的全局变量和静态数据；

#### 7.4 我需要修改代码，但不知道要编写哪些测试？

听起来可能很奇怪，但是自动化单元测试并不是用来发现缺陷的。在修改遗留代码的过程中，自动化测试是用来保证已有的功能不被改变，或者说提供了一种安全网。所以我们至少应该包括两种类型的测试：
**特性测试**
特性测试固定当前系统行为的工具，它可以确保我们不破坏当前系统行为。具体做法请参考实践。
**定向测试**
针对我们要做的修改，覆盖修改内容的测试。

#### 7.5 我们对代码理解不够，所以无法修改

每个人心中都有一个杀不死的恶魔。修改代码之所以恐怖，就在于我们不理解现在的代码。我们可以采取如下措施：
**做笔记、画草图**
当阅读让人迷惑的代码时，首先画些草图，做些笔记会很有用。写下你看到的重要内容的名称，如果两个名称之间有联系，就画条线。我们可以使用标准的UML，或者就是简单的圆圈和线条，这只是让我们保持头脑清醒地一种方式。

**理解性重构**
重构是理解代码的最佳技术之一。没有测试的重构是有很风险的操作，但是只要不提交代码，就不会造成破坏性。你可以按照重构的方式提取方法、移动代码、重命名变量，等到你充分理解代码以后回滚所有变更。

#### 7.6 我想改进代码，但我不知道有没有造成任何破坏
我们有以下措施来保证尽量减少出错：

**超感编辑**
所谓超感编辑就是准确地知道每次敲击键盘时都知道在做什么。结对编程和TDD能让我们达到超感编辑的状态。

**单一目标编辑**
作为程序员，我们应该时刻提醒自己“编程是每次只做一件事的技术”。当我们结对时，总是会让搭档帮忙确认，“你在做什么？”如果答案超过一件事，那么就从中选择一件。

**使用自动化重构工具**
使用现代IDE自动重构功能帮助我们完成修改。

**结对编程**
找一个小伙伴，让他来掩护你。