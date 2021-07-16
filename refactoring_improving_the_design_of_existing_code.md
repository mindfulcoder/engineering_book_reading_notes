# 一、理解重构

## 1、什么是重构？

**Refactor  重构（名词）**：

A change made to the internal structure of software to make it easier to understand and cheaper to modify without changing its observable behavior。

对软件内部结构进行的一种调整，目的是在不改变软件可观察行为的前提下，提高其可理解性，降低其修改成本。

**Refactor  重构（动词）：**

To restructure software by applying a series of refactorings without changing its observable behavior。

使用一系列的重构手法，在不改变软件可观察行为的前提下，调整其结构。

**重构(Refactor)与重写(Rewrite)是容易混淆的概念。**

一些简单的区别就是：

1. 重构是一种工程实践，而重写是一个项目。
2. 重构不会导致持续集成失败，因为每次重构都需要通过自动化测试。
3. 重构的目标是整洁代码和设计模式。
4. 如果软件的功能完全不可用，则通常无法进行重构。

注意：如果系统的业务知识本身仅仅存在于现有代码中，则重写是极度危险的，且鲜有成功案例。

## 2、为什么要重构？

### 2.1 **重构改善了系统设计**

如果没有重构，程序的设计就会逐渐腐败变质。当人们只为短期目标，或者在没有完全理解整体设计之前，就贸然修改代码，程序就会逐渐失去自己的结构。

### 2.2 **重构使软件更易于理解**

如果没有重构，程序就会变得越来越难以被理解，从而使得修改所花费的时间越来越长。重构过程也是理解代码的过程，因为只有代码才是最具体的设计。

### 2.3 **重构帮助减少缺陷**

代码越容易理解，则隐藏其中的缺陷就越容易被发现。

### 2.4 **重构提升开发效率**

良好的设计是快速开发的根本。如果没有良好的设计，即便一开始可以开发的很快，但是随着代码的腐败，最终开发会逐步陷入泥潭。

## 3、什么时候进行重构？

### 3.1 **准备型重构：添加新功能前进行重构**

重构的直接原因是我们需要理解要修改的代码，只有理解了代码，我们才能够很轻松的添加新的功能。

### 3.2 **理解型重构：修复缺陷时进行重构**

现缺陷是代码不够清晰的一个信号，重构过程不但加速缺陷修复，而且能减少以后出现代码缺陷的可能性。

### 3.3 **清理型重构：理解代码功能后进行重构**

如果对于实现方式不够满意，则及时进行清理，保证不会影响下一步开发。

### 3.4 **评审型重构：代码评审时进行重构**

在代码评审时进行重构，可以得到关于代码改进的具体的建议。通过结对编程将重构的代码评审功效发挥到极致。

以上重构时机都是机会性的，也就是作为软件开发过程中的一个步骤随时开展。通常，不应该把重构看做有计划的偿还技术债务的措施；但是，也难以避免有计划的针对复杂功能进行重构。

## 4、什么时候不应该进行重构？

1. 如果软件根本就不能正常工作，则不应该重构。
2. 如果重写的成本远远低于重构，且已经尝试过重构不可行，则不应该重构（这可能是一个艰难的决定）。
3. 对于本次不需要修改的代码，也不需要理解的代码，不需要重构，至少不需要立即重构。
4. 在接近项目上线时，不应该进行重构。此时往往为时已晚，冒险重构反而可能导致灾难性后果。

注意：微服务架构极大降低了重写的风险，但是重构依然是优化代码结构主要手段。

## 5、重构面临的问题

### 5.1 **重构会降低新功能的开发效率吗？**

重构的根本原因是通过调整代码结构，避免代码腐败，从而在长期维护中加快的开发速度。软件的维护成本远远大于软件的初次开发成本，从长远来看，能够更快地修复缺陷、添加新功能才是降低成本的关键。因此，重构在经济上的意义远远大于学术上的意义。

### 5.2 **代码所有权之争**

有时，开发团队外部的人员无法改动本团队所负责系统的源代码；甚至，即使在同一个团队内部的开发人员也没有权限修改其他人负责的代码。这样的代码所有权会严重阻碍重构的开展，其解决之道就在于团队共同负责代码，甚至是考虑组织内部采用开源模式。

### 5.3 **需要建立重构分支吗？**

重构分支本质上就是特性分支，可以短时间存在，但是其存活时间越长则归并难度越大，失败的可能性就越高。更好的方式是基于主干的开发，频繁地进行重构，频繁地进行集成。

### 5.4 **构建自动化测试**

重构的首要前提是拥有一套可靠的测试。自动化测试能够快速发现重构过程中发生的错误，从而保证重构不会破坏系统的可观测行为。

### 5.5 **历史遗留代码**

重构可以作为理解历史遗留代码的工具，甚至是拯救历史遗留代码的手段。

但是，难题在于历史遗留代码往往没有自动化测试，甚至是无法添加自动化测试。因为，可测性是软件设计的一个重要方面，而这可能正好就是历史遗留代码所缺少的。

针对遗留代码的重构，一个建议就是：
1）在没有自动化测试的情况下，为系统划分内部模块--总能找到一些接缝（seam）；
2）为这些接缝定义接口，添加自动化测试，使其成为可测试的模块；
3）针对这些模块进行重构；

通常这是一种极度困难且危险的操作，需要很高的技巧和勇气，也需要一个长期的过程。

### 5.6 **数据库**

数据库重构自身就是一门独立的学科，其中最著名的著作就是《Refactoring Database: Evolutionary   Database Design》, 其核心思想是数据结构变更与数据迁移脚本结合，进行渐进式变更。

### 5.7 **重构、架构和过度设计(YAGNI)**

重构不但使得软件架构能够适应变化，而且还导致软件架构也是逐渐演进的。重构与过度设计之间需要保持一种平衡：既保证当前的功能以一种清晰的逻辑来实现，又保证将来的变化容易进行，适可而止。

### 5.8 **重构与敏捷软件开发**

普遍认为，重构是敏捷软件开发中的核心实践，这就要求开发团队具有敏捷的精神，并且在日常工作中应用敏捷的工程实践。

### 5.9 **重构与性能**

真正影响系统性能的代码往往只占很少一部分，清晰的设计即使在短期内造成一定程度地性能减低，从长远来看反倒是有利于性能调优的。一个广泛接受的观点是，软件开发过程中依次实现：

1. Make it work
2. Make it right
3. Make it fast

### 5.10 **自动化重构工具**

目前流行的开发工具如Intellij Idea、Eclipse等都具备自动化重构的功能，极大方便了开发人员。一些曾经复杂的重构，现在仅仅是一个快捷键而已。熟悉使用自动化重构工具能够极大地提升重构的效率。



# 二、代码的坏味道

### 1. 诡异的命名（Mysterious Name)

名称无法说明意图，甚至导致歧义。

### 2. 重复代码（Duplicated code）

同样的代码结构或者处理逻辑不止在一个地方出现。

### 3. 过长的函数（Long Method）

函数越长则越难理解。过长的函数通常包含了太多的代码行数和局部变量，复杂度很高。

### 4. 过长的参数列表（Long Parameter List）

过长的参数列表导致参数自身的含义难以理解，过长的参数列表也是缺乏封装的体现。

### 5. 全局变量（Global Data）

从程序设计语言发展的早期开始我们就不停地和全局变量做斗争，他们往往就是罪恶的源头。

### 6. 可变数据 （Mutable Data)

数据在一个地方被修改以后又被传到另外一个地方使用，往往造成了意料不到的结果。

### 7. 发散式变化（Divergent Change）

当一个模块的变化总是由于不同的原因或者不同的方式导致时，则这个模块职责不单一。

### 8. 散弹式修改 （Shotgun Surgery）

每次发生变化时，一处变化总会导致其他各处都需要变化，且很难发现所有需要变化的位置。

### 9. 依恋情节（Feature Envy）

一个模块的方法对于属于其他模块的数据更加感兴趣。

### 10. 数据泥潭（Data Clumps）

一些数据（字段，参数列表...）总是喜欢呆在一起。

### 11. 基础类型偏执（Primitive Obsession）

总是喜欢使用基础类型（int、long、string、list、map...）替代小的对象。

### 12. Switch重现（Repeated Switches ）

同一个switch语句总是出现在同一个程序的不同地方。

### 13. 过度使用循环（Loops）

程序中太多的循环造成了逻辑的隐藏。使用Pipeline处理更加清晰。

### 14. 冗余模块（Lazy Element）

一个模块没有什么用处，比如一个类只有一个函数，且只被一个地方使用。

### 15. 夸夸其谈的未来性（Speculative Generality）

为了将来“可能”出现的情况所设计的钩子和特殊处理，但谁也无法肯定将来一定会出现这种情况。

### 16. 令人迷惑的临时字段（Temporary Field）

只在特定情况下才会被赋值和使用的类成员变量。

### 17. 过度耦合的消息链（Message Chain）

调用者让被调用者查询一个内部对象，然后继续向这个内部对象查询另外一个内部对象......从而形成一个很长的消息链。

### 18. 中间人（Middle Man）

一个类型将其大部分功能都代理给其他类型。

### 19. 内幕交易（Insider Trade）

模块之间都太多不透明的交互，即不是通过明面的接口进行的，造成两个模块之间严重耦合。

### 20. 过大的类（Large Classes）

当一个类尝试做太多的事情，通常表现为太多的字段。此时，重复代码随之而来。

### 21. 异曲同工的类（Alternative Classes with Different Interfaces）

两个功能相似的类却实现了不同的接口。

### 22. 幼稚的数据类（Data Class）

有一些类型仅有数据字段和Getter/Setter方法，甚至是有public的字段，这种类型通常不堪大用。一种例外就是纯数据传输类型（record），但是这种数据类通常是不可修改的。

### 23. 被拒绝的馈赠（Refused Bequest）

子类不想使用父类提供的数据和方法。

### 24. 多余的注释（Comments）

Not all comments but the ones that are there because the code is bad.

这种注释存在的原因仅仅因为代码本身很烂。

# 三、重构的方法

## 1. 基础重构方法

### 1.1 提取函数（Extract Function）

**动机**

- 使用良好的命名来表示函数意图，提升代码的可读性；
- 小函数提高代码重用的可能性；
- 如果函数粒度都很小，那么重构代码也变得很容易；
- 高抽象层级的代码调用这样的小函数，其逻辑就会清晰得像一行行注释；

From

```javascript
function printOwing(invoice) {
    let outstanding = 0;
    console.log("***********************");
    console.log("**** Customer Owes ****");
    console.log("***********************");
    // calculate outstanding
    for (const o of invoice.orders) {
        outstanding += o.amount;
    }
    // record due date
    const today = Clock.today;
    invoice.dueDate = new Date(today.getFullYear(), today.getMonth(), today.getDate());
    //print details
    console.log(`name: ${invoice.customer}`);
    console.log(`amount: ${outstanding}`);
    console.log(`due: ${invoice.dueDate.toLocaleDateString()}`);
}
```

to

```javascript
function printOwing(invoice) {
    printBanner();
    const outstanding = calculateOutstanding(invoice);
    recordDueDate(invoice);
    printDetails(invoice, outstanding);
}

function printBanner() {
    console.log("***********************");
    console.log("**** Customer Owes ****");
    console.log("***********************");
}

function calculateOutstanding(invoice) {
    let result = 0;
    for (const o of invoice.orders) {
        result += o.amount;
    }
    return result;
}

function recordDueDate(invoice) {
    const today = Clock.today;
    invoice.dueDate = new Date(today.getFullYear(), today.getMonth(), today.getDate());
}

function printDetails(invoice, outstanding) {
    console.log(`name: ${invoice.customer}`);
    console.log(`amount: ${outstanding}`);
    console.log(`due: ${invoice.dueDate.toLocaleDateString()}`);
}
```



### 1.2 内联函数（Inline Function）

**动机**

- 如果一个功能显而易见时，将其委派给一个小函数的意义不大。
- 当一组函数被过度拆分时，把他们组合起来反而更加清晰。

From

```javascript
function rating(aDriver) {
    return moreThanFiveLateDeliveries(aDriver) ? 2 : 1;
}

function moreThanFiveLateDeliveries(aDriver) {
    return aDriver.numberOfLateDeliveries > 5;
}
```

to

```javascript
function rating(aDriver) {
    return aDriver.numberOfLateDeliveries > 5 ? 2 : 1;
}
```



### 1.3  提取变量（Extract Variable）

**动机**

1. 复杂的表达式很难以理解，引入变量可以通过变量名阐明其含义；
2. 引入变量也方便进行调试；

From

```javascript
function price(order) {
    return order.quantity * order.itemPrice - Math.max(0, order.quantity - 500) * order.itemPrice + Math.min(order.quantity * order.itemPrice * 0.1, 100);
}
```

to

```javascript
function price(order) {
    const basePrice = order.quantity * order.itemPrice;
    const quantityDiscount = Math.max(0, order.quantity - 500) * order.itemPrice;
    const shipping = Math.min(basePrice * 0.1, 100);
    return basePrice - quantityDiscount + shipping;
}
```



### 1.3  内联变量（Inline Variable）

**动机**

- 变量的名称所代表的含义还没有表达式本身清楚，反而成为重构附近代码的障碍；

From

```javascript
let basePrice=order.basePrice;
return basePrice>1000;
```

to

```javascript
return order.basePrice>1000;
```



### 1.4  修改函数申明（Change Function Declaration)

**动机**
1. 良好的函数命名能够揭示函数意图；
2. 恰当的参数列表和命名一样，使得函数易于使用；

From

```javascript
function c(r) {
    return 2 * Math.PI * r;
}
```

to

```javascript
function circumference(radius) {
    return 2 * Math.PI * radius;
}
```



### 1.5  封装变量访问（Encapsulate Variable）

**动机**

1. 函数调用优于直接操作数据，因为可以轻易地将函数调用委派给其他函数；
2. 通过函数访问数据也提供了一个监控数据访问的切入点；

From

```javascript
let defaultOwner = {firstName: "Martin", lastName: "Fowler"};
spaceship.owner = defaultOwner;
```

to

```javascript
let defaultOwnerData = {firstName: "Martin", lastName: "Fowler"};

export function defaultOwner() { return new Person(defaultOwnerData); }
export function setDefaultOwner(arg) { defaultOwnerData = arg; }

class Person {
    constructor(data) {
        this._lastName = data.lastName;
        this._firstName = data.firstName
    }
    get lastName() { return this._lastName; }
    get firstName() { return this._firstName; }
}
```



### 1.6 重命名变量（Rename Variable)

**动机**

1. 良好的命名是整洁代码的核心，良好的命名能够揭示意图；

From

```javascript
let tpHd = "untitled";
result += `<h1>${tpHd}</h1>`;
```

to

```javascript
let title = "untitled";
result += `<h1>${title}</h1>`;
```



### 1.7  引入参数对象（Introduce Parameter Object)

**动机**

1. 参数列表总是同时出现是数据泥潭的体现；
2. 封装参数对象使参数之间的关系更加明朗；
3. 封装参数对象减小了参数列表长度；
4. 封装参数对象便于进一步的重构，如提取函数和提取类；

From

```javascript
const station = {
    name: "ZB1",
    readings: [
        {
            temp: 47, time: "2016111009:10"
        },
        {
            temp: 53, time: "2016111009:20"
        },
    ]
};

function readingsOutsideRange(station, min, max) {
    return station.readings.filter(r => r.temp < min || r.temp > max);
}
```

to

```javascript
const station = {
    name: "ZB1",
    readings: [
        {
            temp: 47, time: "2016111009:10"
        },
        {
            temp: 53, time: "2016111009:20"
        },
    ]
}

class NumberRange {
    constructor(min, max) { this._data = {min: min, max: max}; }
    get min() { return this._data.min; }
    get max() {  return this._data.max; }
    contains(arg) { return (arg >= this.min && arg <= this.max); }
}
function readingsOutsideRange(station, range) {
    return station.readings.filter(r => !range.contains(r.temp));
}
```



### 1.8  将函数聚合成类（Combine Functions To Class）

**动机**

1. 类是面向对象程序设计语言的基本单位，是软件模块化的基本方式；

From

```javascript
const aReading = {customer: "ivan", quantity: 10, month: 5, year: 2017};
const base = (baseRate(aReading.month, aReading.year) * aReading.quantity);
const taxableCharge = Math.max(0, basetaxThreshold(aReading.year));
```

to

```javascript
class Reading {
    constructor(data) {
        this._customer = data.customer;
        this._quantity = data.quantity;
        this._month = data.month;
        this._year = data.year;
    }
    get customer() { return this._customer; }
    
    get quantity() { return this._quantity; }
    
    get month() {  return this._month; }
    
    get year() { return this._year; }
    
    get calculateBaseCharge() { return baseRate(this.month, this.year) * this.quantity; }
    
    get baseCharge() { return baseRate(this.month, this.year) * this.quantity; }
    
    get taxableCharge() { return Math.max(0, this.baseCharge - taxThreshold(this.year)) }
}

const aReading = new Reading({customer: "ivan", quantity: 10, month: 5, year: 2017});
const taxableCharge = aReading.taxableCharge;
```



### 1.9  将函数聚合为变换（Combine Functions Into Transform）

**动机**

1. 数据的计算经常重复出现，将他们聚合在在一起可以避免重复；

From

```javascript
let reading = {customer: "ivan", quantity: 10, month: 5, year: 2017};
const baseCharge = baseRate(reading.month, reading.year) * reading.quantity;
```

to

```javascript
let reading = {customer: "ivan", quantity: 10, month: 5, year: 2017};

function calculateBaseCharge(aReading) {
    return baseRate(aReading.month, aReading.year) * aReading.quantity;
}

function enrichReading(original) {
    const result = _.cloneDeep(original);
    result.baseCharge = calculateBaseCharge(result);
    return result;
}
const aReading = enrichReading(rawReading);
const baseCharge = aReading.baseCharge;
```



### 1.10  拆分阶段（Split Phase）

**动机**

1. 将不同的行为拆分成不同的步骤，以便分而治之；

From

```javascript
function priceOrder(product, quantity, shippingMethod) {
    const basePrice = product.basePrice * quantity;
    const discount = Math.max(quantity - product.discountThreshold, 0) * product.basePrice * product.discountRate;
    const shippingPerCase = (basePrice > shippingMethod.discountThreshold) ? shippingMethod.discountedFee : shippingMethod.feePerCase;
    const shippingCost = quantity * shippingPerCase;
    const price = basePrice - discount + shippingCost;
    return price;
}
```

to

```javascript
function priceOrder(product, quantity, shippingMethod) {
    const priceData = calculatePricingData(product, quantity);
    return applyShipping(priceData, shippingMethod);
}

function calculatePricingData(product, quantity) {
    const basePrice = product.basePrice * quantity;
    const discount = Math.max(quantity - product.discountThreshold, 0) * product.basePrice * product.discountRate;
    return {basePrice: basePrice, quantity: quantity, discount: discount};
}

function applyShipping(priceData, shippingMethod) {
    const shippingPerCase = (priceData.basePrice > shippingMethod.discountThreshold)
        ? shippingMethod.discountedFee : shippingMethod.feePerCase;
    const shippingCost = priceData.quantity * shippingPerCase;
    return priceData.basePrice
    priceData.discount + shippingCost;
}
```



## 2. 封装

### 2.1  封装数据记录（Encapsulate Record）

**动机**

1. 将数据封装成数据记录便于隐藏内部数据、提供访问方法、跟踪调用者；
2. 将数据封装成数据记录便于数据的序列化和反序列化；

From

```javascript
const organization = {name: "Acme Gooseberries", country: "GB"};
```

to

```javascript
class Organization {
    constructor(data) {
        this._name = data.name;
        this._country = data.country;
    }
    get name() { return this._name; }
    
    set name(aString) { this._name = aString; }
    
    get country() { return this._country; }
    
    set country(aCountryCode) { this._country = aCountryCode; }
}

const organization = new Organization({name: "Acme Gooseberries", country: "GB"});
function getRawDataOfOrganization() { return organization._data; }
function getOrganization() { return organization; }
```



### 2.2   封装对集合访问（Encapsulate Collection）

**动机**

1. 控制调用者对内部数据结构的访问，避免避免调用者直接修改内部数据结构；

From

```javascript
class Person {
    constructor(name) {
        this._name = name;
        this._courses = [];
    }
    get name() { return this._name;}
    
    get courses() { return this._courses;}
    
    set courses(aList) { this._courses = aList;}
}

class Course {
    constructor(name, isAdvanced) {
        this._name = name;
        this._isAdvanced = isAdvanced;
    }
    get name() { return this._name; }
    
    get isAdvanced() { return this._isAdvanced;}
}

for (const name of readBasicCourseNames(filename)) {
    aPerson.courses.push(new Course(name, false));
}
```

to

```javascript
class Person {
    constructor(name) {
        this._name = name;
        this._courses = [];
    }
    get name() { return this._name; }
    
    get courses() { return this._courses.slice(); }
    
    set courses(aList) { this._courses = aList.slice(); }
    
    addCourse(aCourse) { this._courses.push(aCourse); }
    
    removeCourse(aCourse, fnIfAbsent = () => { throw new RangeError();}) {
        const index = this._courses.indexOf(aCourse);
        if (index === 1)
            fnIfAbsent();
        else this._courses.splice(index, 1);
    }
}

class Course {
    constructor(name, isAdvanced) {
        this._name = name;
        this._isAdvanced = isAdvanced;
    }
    get name() { return this._name; }
    
    get isAdvanced() { return this._isAdvanced; }
}

for(const name of readBasicCourseNames(filename)) {
    aPerson.addCourse(new Course(name, false));
}
```

### 2.3  使用对象替代基本类型(Replace Primitive With Object)

**动机**

1. 使用对象类型更容易添加业务相关行为，从而形成业务对象；

From

```javascript
class Order {
    constructor(data) {
        this.priority = data.priority;
    }
}

highPriority = orders.filter(o => "high" === o.priority || "rush" === o.priority).length;
```

to

```javascript
class Order {
    constructor(data) {
        this.priority = data.priority;
    }
    get priorityString() { return this._priority.toString(); }
    
    set priority(aString) { this._priority = new Priority(aString); }
    
    set priority(aString) { this._priority = new Priority(aString);}
}

class Priority {
    constructor(value) {
        if (value instanceof Priority) return value;
        if (Priority.legalValues().includes(value))
            this._value = value;
        else
            throw new Error(`<${value}> is invalid for Priority`);
    }

    toString() { return this._value; }
    
    get _index() { return Priority.legalValues().findIndex(s => s === this._value); }
    
    static legalValues() { return ['low', 'normal', 'high', 'rush']; }
    
    equals(other) { return this._index === other._index; }
    
    higherThan(other) { return this._index > other._index; }
    
    lowerThan(other) { return this._index < other._index; }
}

highPriority = orders.filter(o => o.priority.higherThan(new Priority("normal")).length;
```



### 2.4  以查询取代临时变量（ Replace Temp with Query）
**动机**

- 使用查询函数替代临时变量，则同一个模块中的其他函数都可以利用这个函数。
- 这是提取函数前的重要步骤。

From

```javascript
class Order {
    constructor(quantity, item) {
        this._quantity = quantity;
        this._item = item;
    }

    get price() {
        let basePrice = this._quantity * this._item.price;
        let discountFactor = 0.98;
        if (basePrice > 1000) {
            discountFactor = 0.03;
        }
        return basePrice * discountFactor;
    }
}
```
to

```javascript
class Order {
    constructor(quantity, item) {
        this._quantity = quantity;
        this._item = item;
    }

    get basePrice() {
        return this._quantity * this._item.price;
    }
    
    get discountFactor() {
        let discountFactor = 0.98;
        if (this.basePrice > 1000) discountFactor = 0.03;
        return discountFactor;
    }

    get price() {
        return this.basePrice * this.discountFactor;
    }
}
```



### 2.5  提取类（Extract Class）

**动机**

1. 随着功能不断增加，类的职责逐渐不单一，拆分类才能明确职责；
2. 类的部分方法和数据会倾向于单独行动，此时应该进行拆分；

```javascript
class Person {
    constructor(name,officeAreaCode,officeNumber) {
        this._name=name;
        this._officeAreaCode=officeAreaCode;
        this._officeNumber=officeNumber;
    }
    get name() { return this._name; }
    
    set name(arg) { this._name = arg; }
    
    get telephoneNumber() { return `(${this.officeAreaCode}) ${this.officeNumber}`; }
    
    get officeAreaCode() { return this._officeAreaCode; }
    
    set officeAreaCode(arg) { this._officeAreaCode = arg; }
    
    get officeNumber() { return this._officeNumber; }
    
    set officeNumber(arg) { this._officeNumber = arg; }
}
```

to

```javascript
class TelephoneNumber {
    constructor(officeAreaCode, officeNumber) {
        this._officeAreaCode = officeAreaCode;
        this._officeNumber = officeNumber;
    }

    get officeAreaCode() { return this._officeAreaCode;}
    
    get officeNumber() {return this._telephoneNumber.officeNumber;}
    
    get telephoneNumber() {return `(${this.officeAreaCode}) ${this.officeNumber}`;}
}

class Person {
    constructor(name,telephoneNumber) {
        this._name=name;
        this._telephoneNumber=telephoneNumber;
    }
    get name() { return this._name; }

    get telephoneNumber() {return this._telephoneNumber.telephoneNumber;}

}
```



### 2.6  内联类（Inline Class）

**动机**

1. 经过提取新类，原类的职责逐渐减少，遗留功能逐渐没有必要作为独立类；
2. 当两个类的功能存在交织，需要重新划分时，先进行内联，再进行拆分；

From

```javascript
class TrackingInformation {
    get shippingCompany() { return this._shippingCompany;}

    set shippingCompany(arg) { this._shippingCompany = arg; }

    get trackingNumber() { return this._trackingNumber; }

    set trackingNumber(arg) { this._trackingNumber = arg; }

    get display() { return `${this.shippingCompany}: ${this.trackingNumber}`; }
}

class Shipment {
    get trackingInfo() {
        return this._trackingInformation.display;
    }
    get trackingInformation() {return this._trackingInformation;}
    set trackingInformation(info) { this._trackingInformation = info;}
}
```

to

```javascript
class Shipment {
    get trackingInfo() { return `${this.shippingCompany}: ${this.trackingNumber}`;}

    get shippingCompany() { return this._shippingCompany; }

    set shippingCompany(arg) { this._shippingCompany = arg;}

    get trackingNumber() { return this._trackingNumber; }

    set trackingNumber(arg) { this._trackingNumber = arg;}
}
```



### 2.7. 隐藏代理关系（Hide Delegate）

**动机**

1. 隐藏调用者不必知道的信息，可以减少变更对调用者的影响；

From

```javascript
class Person {
    constructor(name,department) {
        this._name = name;
        this._department = department;
    }

    get name() { return this._name; }

    get department() { return this._department; }

    set department(arg) { this._department = arg; }
}

class Department {
    get chargeCode() { return this._chargeCode; }

    set chargeCode(arg) { this._chargeCode = arg; }

    get manager() { return this._manager; }

    set manager(arg) { this._manager = arg; }
}

manager = aPerson.department.manager;
```

to

```javascript
class Person {
    constructor(name,department) {
        this._name = name;
        this._department = department;
    }

    get name() { return this._name; }

    get department() { return this._department; }

    set department(arg) { this._department = arg; }

    get manager() {return this._department.manager;}
}

class Department {
    get chargeCode() { return this._chargeCode; }

    set chargeCode(arg) { this._chargeCode = arg; }

    get manager() { return this._manager; }

    set manager(arg) { this._manager = arg; }
}

manager = aPerson.manager;
```



### 2.8  移除中间人（Remove Middle Man）

**动机**

1. 隐藏的代理功能越多，服务方就越容易失去自我的功能，变成纯粹的代理；

From

```javascript
class Person {
    constructor(name,department) {
        this._name = name;
        this._department = department;
    }

    get name() { return this._name; }

    get department() { return this._department; }

    set department(arg) { this._department = arg; }

    get manager() {return this._department.manager;}
}

class Department {
    get chargeCode() { return this._chargeCode; }

    set chargeCode(arg) { this._chargeCode = arg; }

    get manager() { return this._manager; }

    set manager(arg) { this._manager = arg; }
}

manager = aPerson.manager;
```

to

```javascript
class Person {
    constructor(name,department) {
        this._name = name;
        this._department = department;
    }

    get name() { return this._name; }

    get department() { return this._department; }

    set department(arg) { this._department = arg; }
}

class Department {
    get chargeCode() { return this._chargeCode; }

    set chargeCode(arg) { this._chargeCode = arg; }

    get manager() { return this._manager; }

    set manager(arg) { this._manager = arg; }
}

manager = aPerson.department.manager;
```



### 2.9  替换算法 （Substitute Algorithm）

**动机**

1. 当一种算法变得越来越复杂时，使用用更简单的方式替换；
2. 当算法变复杂时将很难修改，化简有助于将来的优化；

From

```javascript
function findPerson(people) {
    for (let i = 0; i < people.length; i++) {
        if (people[i] == "Don") {
            return "Don";
        }
        if (people[i] == "John") {
            return "John";
        }
        if (people[i] == "Kent") {
            return "Kent";
        }
    }
    return "";
}
```

to

```javascript
function findPerson(people) {
    const candidates = ["Don", "John", "Kent"];
    return people.find(p => candidates.includes(p)) || "";
}
```


## 3. 移动特性

### 3.1 移动函数（Move Function）

**动机**

1. 将相关的功能聚合在一起，提升模块化程度；
2. 随着软件功能的变化，函数的功能和上下文也发生了变化；
3. 因为调用方发生了变化，函数需要改变以便使用；

例子：

1. 移动内嵌函数；
2. 在类之间移动函数；

From

```java
class Class1 {
	  aMethod()
	}

class Class2 {	}
```
to


```java
class Class1 {	}

class Class2 {
	  aMethod()
	}
```

### 3.2 移动字段（Move Field）

**动机**

1. 数据结构与代表的业务逻辑不一致，容易造成误解；
2. 将数据与其相关的功能聚合在一起，提升聚合度；

```java
class Class1 {
	aField
}

class Class2 {	}
```
to


```java
class Class1 {	}
class Class2 {
	  aField
}
```



### 3.3 将表达式移动到函数（Move Statement Into Function）

**动机**

1. 如果表达式总是伴随函数调用出现，则可能表达式本身应该是被调用函数的一部分；

From

```javascript
function renderPerson(outStream, person) {
    const result = [];
    result.push(`<p>${person.name}</p>`);
    result.push(renderPhoto(person.photo));
    result.push(`<p>title: ${person.photo.title}</p>`);
    result.push(emitPhotoData(person.photo));
    return result.join("\n");
}

function photoDiv(p) {
    return [
        "<div>",
        `<p>title: ${p.title}</p>`,
        emitPhotoData(p),
        "</div>",
    ].join("\n");
}

function emitPhotoData(aPhoto) {
    const result = [];
    result.push(`<p>location: ${aPhoto.location}</p>`);
    result.push(`<p>date: ${aPhoto.date.toDateString()}</p>`);
    return result.join("\n");
}
```

to

```javascript
function renderPerson(outStream, person) {
    const result = [];
    result.push(`<p>${person.name}</p>`);
    result.push(renderPhoto(person.photo));
    result.push(emitPhotoData(person.photo));
    return result.join("\n");
}

function photoDiv(aPhoto) {
    return [
        "<div>",
        emitPhotoData(aPhoto),
        "</div>",
    ].join("\n");
}

function emitPhotoData(aPhoto) {
    return [
        `<p>title: ${aPhoto.title}</p>`,
        `<p>location: ${aPhoto.location}</p>`,
        `<p>date: ${aPhoto.date.toDateString()}</p>`,
    ].join("\n");
}
```



### 3.4 将表达式移动到调用者（Move Statement To Caller）

**动机**

1. 随着软件功能的变化，原本聚合度高的函数逐渐拥有多重职责，则考虑将部分功能移到调用者；

From

``` javascript
function renderPerson(outStream, person) {
    outStream.write(`<p>${person.name}</p>\n`);
    renderPhoto(outStream, person.photo);
    emitPhotoData(outStream, person.photo);
}

function listRecentPhotos(outStream, photos) {
    photos
        .filter(p => p.date > recentDateCutoff())
        .forEach(p => {
            outStream.write("<div>\n");
            emitPhotoData(outStream, p);
            outStream.write("</div>\n");
        });
}

function emitPhotoData(outStream, photo) {
    outStream.write(`<p>title: ${photo.title}</p>\n`);
    outStream.write(`<p>date: ${photo.date.toDateString()}</p>\n`);
    outStream.write(`<p>location: ${photo.location}</p>\n`);
}
```

To

```javascript
function renderPerson(outStream, person) {
    outStream.write(`<p>${person.name}</p>\n`);
    renderPhoto(outStream, person.photo);
    emitPhotoData(outStream, person.photo);
    outStream.write(`<p>location: ${person.photo.location}</p>\n`);
}

function listRecentPhotos(outStream, photos) {
    photos
        .filter(p => p.date > recentDateCutoff())
        .forEach(p => {
            outStream.write("<div>\n");
            emitPhotoData(outStream, p);
            outStream.write(`<p>location: ${p.location}</p>\n`);
            outStream.write("</div>\n");
        });
}

function emitPhotoData(outStream, photo) {
    outStream.write(`<p>title: ${photo.title}</p>\n`);
    outStream.write(`<p>date: ${photo.date.toDateString()}</p>\n`);
}
```

### 3.5  将内联代码替换为函数调用（Replace Inline Code With Function Call）

**动机**

1. 通过函数调用可以减少重复代码，降低代码复杂度；
2. 函数名称能揭示操作内涵，提升可读性；
3. 使用库函数可以避免重复造轮子；

From

```javascript
let appliesToMass = false;
for (const s of states) {
    if (s === "MA") appliesToMass = true;
}
```

to

```javascript
appliesToMass = states.includes("MA");
```



### 3.6 移动表达式（Slide Statements）

**动机**

1. 将关联性高的表达式互相靠近，从而提升可读性；
2. 将变量申明与变量使用尽量靠近，更容促成其他重构；

From

```javascript
const pricingPlan = retrievePricingPlan();
const order = retreiveOrder();
let charge;
const chargePerUnit = pricingPlan.unit;
```

to

```javascript
const pricingPlan = retrievePricingPlan();
const chargePerUnit = pricingPlan.unit;
const order = retreiveOrder();
let charge;
```



### 3.7 拆分循环（Split Loop）

**动机**

1. 在同一个循环中进行的两种操作应该拆分成两个循环分别进行；

From

```javascript
let averageAge = 0;
let totalSalary = 0;
for (const p of people) {
    averageAge += p.age;
    totalSalary += p.salary;
}
averageAge = averageAge / people.length;
```

to

```javascript
let totalSalary = 0;
for (const p of people) {
    totalSalary += p.salary;
}
let averageAge = 0;
for (const p of people) {
    averageAge += p.age;
}
averageAge = averageAge / people.length;
```



### 3.8 使用Pipeline替代循环（Replace Loop With Pipeline）

**动机**

1. 使用Pipeline时比传统的循环可读性更强；

```javascript
function acquireData(input) {
    const lines = input.split("\n");
    let firstLine = true;
    const result = [];
    for (const line of lines) {
        if (firstLine) {
            firstLine = false;
            continue;
        }
        if (line.trim() === "") continue;
        const record = line.split(",");
        if (record[1].trim() === "India") {
            result.push({ city: record[0].trim(), phone: record[2].trim() });
        }
    }
    return result;
}
```

to

```javascript
function acquireData(input) {
    const lines = input.split("\n");
    return lines
        .slice(1)
        .filter(line => line.trim() !== "")
        .map(line => line.split(","))
        .filter(fields => fields[1].trim() === "India")
        .map(fields => ({ city: fields[0].trim(), phone: fields[2].trim() }));
}
```



### 3.9 移除无用代码（Remove Dead Code）

**动机**

1. 执行路径不可达的代码会造成歧义，影响可读性；
2. 废弃的代码应该尽快删除，不能只是注释掉，否则容易让其他开发任意疑惑；

From

```javascript
if(false) {
  doSomethingThatUsedToMatter();
}
```

to

```javascript

```

## 4. 组织数据



### 4.1  拆分变量（Split Variable）

**动机**

* 变量不应该有多个职责，阅读代码时很容易产生困惑。例如：除循环变量外，一个变量不应该被多次赋值；同一个变量不应代表多重含义；

From

```javascript
let temp = 2 * (height + width);
console.log(temp);
temp = height * width;
console.log(temp);
```
to
```javascript
const perimeter = 2 * (height + width);
console.log(perimeter);
const area = height * width;
console.log(area);
```



### 4.2 重命名字段（Rename Field）

**动机**

1. 字段名对数据结构至关重要，良好的命名能够揭示内涵，从而提升可读性和可维护性；

From

```javascript
class Org {
    constructor(data) {
        this._n = data.n;
        this._c = data.c;
    }
    get n() { return this._n; }
    set n(aString) { this._n = aString; }
    get c() { return this._c; }
    set c(aCountryCode) { this._c = aCountryCode; }
}
const org = new Org({ n: "Acme Gooseberries", c: "GB" });
```

to

```javascript
class Organization {
    constructor(data) {
        this._name = data.name;
        this._country = data.country;
    }
    get name() { return this._name; }
    set name(aString) { this._name = aString; }
    get country() { return this._country; }
    set country(aCountryCode) { this._country = aCountryCode; }
}
const organization = new Organization({ name: "Acme Gooseberries", country: "GB" });
```



### 4.3 将派生变量替换为查询（Replace Derived Variable With Query）

**动机**

1. 减少派生的本地变量，从而减少可修改状态；
2. 如果派生的变量是不可修改的，则应该尽量减小其作用域；

From

```javascript
get discountedTotal() { return this._discountedTotal; }
set discount(aNumber) {
    const old = this._discount;
    this._discount = aNumber;
    this._discountedTotal += old - aNumber;
}
```

to

```javascript
get discountedTotal() {return this._baseTotal - this._discount;}
set discount(aNumber) {this._discount = aNumber;}
```



### 4.4 将引用对象转换为值对象（Replace Reference With Value）

**动机**

1. 将内嵌数据结构当做不可修改的值对象，可以避免外部对于引用对象的修改；
2. 对于内部嵌套对象的修改，总是新建一个新的对象，可以避免外部修改带来的影响；

From

```javascript
class Person {
    constructor() {
        this._telephoneNumber = new TelephoneNumber();
    }
    get officeAreaCode() { return this._telephoneNumber.areaCode; }
    set officeAreaCode(arg) { this._telephoneNumber.areaCode = arg; }
    get officeNumber() { return this._telephoneNumber.number; }
    set officeNumber(arg) { this._telephoneNumber.number = arg; }
}

class TelephoneNumber {
    constructor(areaCode, number) {
        this._areaCode = areaCode;
        this._number = number;
    }
    get areaCode() { return this._areaCode; }
    set areaCode(arg) { this._areaCode = arg; }
    get number() { return this._number; }
    set number(arg) { this._number = arg; }
}
```

to

```javascript
class Person {
    constructor() {
        this._telephoneNumber = new TelephoneNumber();
    }
    get officeAreaCode() { return this._telephoneNumber.areaCode; }
    set officeAreaCode(arg) {
        this._telephoneNumber = new TelephoneNumber(arg, this.officeNumber);
    }
    get officeNumber() { return this._telephoneNumber.number; }
    set officeNumber(arg) {
        this._telephoneNumber = new TelephoneNumber(this.officeAreaCode, arg);
    }
}

class TelephoneNumber {
    constructor(areaCode, number) {
        this._areaCode = areaCode;
        this._number = number;
    }
    get areaCode() { return this._areaCode; }
    set areaCode(arg) { this._areaCode = arg; }
    get number() { return this._number; }
    set number(arg) { this._number = arg; }
}
```



### 4.5 将值对象转换为引用（Replace Value With Reference）

**动机**

1. 同一份数据被多处使用，如果需要修改，则存在多个副本会造成麻烦，此时应该使用引用替换值对象；

From

```javascript
let customer = new Customer(customerData);
```

to

```javascript
let customer = customerRepository.get(customerData.id);
```



## 5. 简化条件判断



### 5.1 分解条件（Decompose Conditional）

**动机**

1. 复杂和嵌套的条件使得复杂大增加，可读性降低；
2. 分解条件并使用函数替代，可以阐明条件判断的意图，提高可读性；

From

```javascript
if (!aDate.isBefore(plan.summerStart) && !aDate.isAfter(plan.summerEnd))
    charge = quantity * plan.summerRate;
else
    charge = quantity * plan.regularRate + plan.regularServiceCharge;
```

to

```javascript
function summer() {
    return !aDate.isBefore(plan.summerStart) && !aDate.isAfter(plan.summerEnd);
}
function summerCharge() {
    return quantity * plan.summerRate;
}
function regularCharge() {
    return quantity * plan.regularRate + plan.regularServiceCharge;
}
charge = summer() ? summerCharge() : regularCharge();
```



### 5.2  加固条件表达式（Consolidate Conditional Expression）

**动机**

1. 将导致同样结果的不通条件聚合成一个条件，使得逻辑更加清楚；
2. 将聚合在一起的条件提取成为函数，使得代码更加清晰；

From

```javascript
function disabilityAmount(anEmployee) {
    if (anEmployee.seniority < 2) return 0;
    if (anEmployee.monthsDisabled > 12) return 0;
    if (anEmployee.isPartTime) return 0;
    return 1;
    // compute the disability amount
```

to

```javascript
function isNotEligableForDisability() {
    return ((anEmployee.seniority < 2)|| (anEmployee.monthsDisabled > 12)|| (anEmployee.isPartTime));
}
function disabilityAmount(anEmployee) {
    if (isNotEligableForDisability())
        return 0;
    else
        return 1;
}
```



### 5.3 将嵌套条件转换为卫语句（Replace Nested Conditional With Guard Clause）

**动机**

1. 使用卫语句能降低嵌套条件所带来的复杂度；
2. 虽然有违单一出口的观点，但是清晰度才是王道；

From

```javascript
function getPayAmount() {
    let result;
    if (isDead)
        result = deadAmount();
    else {
        if (isSeparated)
            result = separatedAmount();
        else {
            if (isRetired)
                result = retiredAmount();
            else
                result = normalPayAmount();
        }
    }
    return result;
}
```

to

```javascript
function getPayAmount() {
    if (isDead) return deadAmount();
    if (isSeparated) return separatedAmount();
    if (isRetired) return retiredAmount();
    return normalPayAmount();
}
```



### 5.4 使用多态来替代条件判断（Replace Conditional With Polymorphism)

**动机**

1. 多态是面向对象的程序设计语言用于处理复杂度的有力工具，合理使用能降低复杂条件判断的难度；

From

```javascript
function plumages(birds) {
    return new Map(birds.map(b => [b.name, plumage(b)]));
}
function speeds(birds) {
    return new Map(birds.map(b => [b.name, airSpeedVelocity(b)]));
}
function plumage(bird) {
    switch (bird.type) {
        case 'EuropeanSwallow':
            return "average";
        case 'AfricanSwallow':
            return (bird.numberOfCoconuts > 2) ? "tired" : "average";
        case 'NorwegianBlueParrot':
            return (bird.voltage > 100) ? "scorched" : "beautiful";
        default:
            return "unknown";
    }
}
function airSpeedVelocity(bird) {
    switch (bird.type) {
        case 'EuropeanSwallow':
            return 35;
        case 'AfricanSwallow':
            return 40 - 2 * bird.numberOfCoconuts;
        case 'NorwegianBlueParrot':
            return (bird.isNailed) ? 0 : 10 + bird.voltage / 10;
        default:
            return null;
    }
}
```

to

```javascript

class Bird {
    constructor(birdObject) {
        Object.assign(this, birdObject);
    }
    get plumage() {
        return "unknown";
    }
    get airSpeedVelocity() {
        return null;
    }
}
class EuropeanSwallow extends Bird {
    get plumage() {
        return "average";
    }
    get airSpeedVelocity() {
        return 35;
    }
}
class AfricanSwallow extends Bird {
    get plumage() {
        return (this.numberOfCoconuts > 2) ? "tired" : "average";
    }
    get airSpeedVelocity() {
        return 40 - 2 * this.numberOfCoconuts;
    }
}
class NorwegianBlueParrot extends Bird {
    get plumage() {
        return (this.voltage > 100) ? "scorched" : "beautiful";
    }
    get airSpeedVelocity() {
        return (this.isNailed) ? 0 : 10 + this.voltage / 10;
    }
}
function createBird(bird) {
    switch (bird.type) {
        case 'EuropeanSwallow':
            return new EuropeanSwallow(bird);
        case 'AfricanSwallow':
            return new AfricanSwallow(bird);
        case 'NorwegianBlueParrot':
            return new NorwegianBlueParrot(bird);
        default:
            return new Bird(bird);
    }
}

function plumages(birds) {
    return new Map(birds
        .map(b => createBird(b))
        .map(bird => [bird.name, bird.plumage]));
}
function speeds(birds) {
    return new Map(birds
        .map(b => createBird(b))
        .map(bird => [bird.name, bird.airSpeedVelocity]));
}
```



### 5.5 引入特殊案例（Introduce Special Case）

**动机**

1. 将特殊的状态转换为特殊的正常状态，可以减少重复代码，Null判断就是其中一个典型；

From

```javascript
if (aCustomer === "unknown") customerName = "occupant";
```

to

```javascript
class UnknownCustomer {
      get name() {return "occupant";}
}
```



### 5.6 引入断言（Introduce Assert）

**动机**

1. 当某种条件理应成立时，使用断言语句比每次都进行条件判断更加能够简化代码，避免重复；

From

```javascript
class Customer {
    applyDiscount(aNumber) {
        if (!this.discountRate) {  
            return aNumber - (this.discountRate * aNumber); 
        }
    }
}
```

to

```javascript
class Customer {
    applyDiscount(aNumber) {
         return aNumber - (this.discountRate * aNumber);
    }
    set discountRate(aNumber) {
        assert(null === aNumber || aNumber >= 0);
        this._discountRate = aNumber;
    }
}
```



## 6. 重构API



### 6.1 查询与修改分离（Separate Query From Modifier）

**动机**

1. 仅仅做查询的操作不会产生边际效应，应该和执行修改的操作分离；

From

```javascript
function alertForMiscreant(people) {
    for (const p of people) {
        if (p === "Don") {
            setOffAlarms();
            return "Don";
        }
        if (p === "John") {
            setOffAlarms();
            return "John";
        }
    }
    return "";
}
```

to

```javascript
function findMiscreant(people) {
    for (const p of people) {
        if (p === "Don") {
            return "Don";
        }
        if (p === "John") {
            return "John";
        }
    }
    return "";
}

function alertForMiscreant(people) {
    if (findMiscreant(people) !== "") setOffAlarms();
}
```



### 6.2 参数化函数（Parameterize Function）

**动机**

1. 当两个函数有相似的逻辑，但是使用不同的参数值时，考虑抽象共同的参数后合并函数；

From

```javascript
function tenPercentRaise(aPerson) {
    aPerson.salary = aPerson.salary.multiply(1.1);
}
function fivePercentRaise(aPerson) {
    aPerson.salary = aPerson.salary.multiply(1.05);
}
```

to

```javascript
function raise(aPerson, factor) {
    aPerson.salary = aPerson.salary.multiply(1 + factor);
}
```



### 6.3 移除标志位参数（Remove Flag Argument）

**动机**

1. 标志位参数通常意味着函数的职责不单一，调用者的职责放到了被调用者中；
2. 标志位参数让函数的功能难以理解，而且提高了函数的复杂度；

From

```javascript
function deliveryDate(anOrder, isRush) {
    if (isRush) {
        let deliveryTime;
        if (["MA", "CT"].includes(anOrder.deliveryState)) deliveryTime = 1;
        else if (["NY", "NH"].includes(anOrder.deliveryState)) deliveryTime = 2;
        else deliveryTime = 3;
        return anOrder.placedOn.plusDays(1 + deliveryTime);
    }
    else {
        let deliveryTime;
        if (["MA", "CT", "NY"].includes(anOrder.deliveryState)) deliveryTime = 2;
        else if (["ME", "NH"].includes(anOrder.deliveryState)) deliveryTime = 3;
        else deliveryTime = 4;
        return anOrder.placedOn.plusDays(2 + deliveryTime);
    }
}
```

to

```javascript
function rushDeliveryDate(anOrder) {
    let deliveryTime;
    if (["MA", "CT"].includes(anOrder.deliveryState)) deliveryTime = 1;
    else if (["NY", "NH"].includes(anOrder.deliveryState)) deliveryTime = 2;
    else deliveryTime = 3;
    return anOrder.placedOn.plusDays(1 + deliveryTime);
}
function regularDeliveryDate(anOrder) {
    let deliveryTime;
    if (["MA", "CT", "NY"].includes(anOrder.deliveryState)) deliveryTime = 2;
    else if (["ME", "NH"].includes(anOrder.deliveryState)) deliveryTime = 3;
    else deliveryTime = 4;
    return anOrder.placedOn.plusDays(2 + deliveryTime);
}

if (isRush) {
    deliveryDate = rushDeliveryDate(anOrder);
} else {
    deliveryDate = regularDeliveryDate(anOrder);
}
```



### 6.4 保留整个参数对象（Preserve Whole Object）

**动机**

1. 将整个数据对象作为参数传入函数，比仅抽取部分字段作为参数，有更小的参数列表，更加能够石适应变化；

From

```javascript
const low = aRoom.daysTempRange.low;
const high = aRoom.daysTempRange.high;
if (!aPlan.withinRange(low, high)){
    alerts.push("room temperature went outside range");
}
```

to

```javascript
if (!aPlan.withinRange(aRoom.daysTempRange)){
    alerts.push("room temperature went outside range");
}
```



### 6.5 将参数替换为查询（Replace Parameter With Query）

**动机**

1. 减小函数的参数列表，减少函数的依赖，提升函数可用性；
2. 减少局部变量，因为函数可以直接查询到所需参数；

From

```javascript
class Order {
    get finalPrice() {
        const basePrice = this.quantity * this.itemPrice;
        let discountLevel;
        if (this.quantity > 100) discountLevel = 2;
        else discountLevel = 1;
        return this.discountedPrice(basePrice, discountLevel);
    }
    discountedPrice(basePrice, discountLevel) {
        switch (discountLevel) {
            case 1: return basePrice * 0.95;
            case 2: return basePrice * 0.9;
        }
    }
}
```

to

```javascript
class Order {
    get discountLevel() {
        return (this.quantity > 100) ? 2 : 1;
    }
    get finalPrice() {
        const basePrice = this.quantity * this.itemPrice;
        return this.discountedPrice(basePrice);
    }
    discountedPrice(basePrice) {
        switch (this.discountLevel) {
            case 1: return basePrice * 0.95;
            case 2: return basePrice * 0.9;
        }
    }
}
```



### 6.6 将查询替换为参数（Replace Query With Parameter）

**动机**

1. 减少函数对于全局变量的依赖，使方法变成无状态的纯函数；
2. 减少变量的作用域，以便移动和提取变量；

From

```javascript
class HeatingPlan {
    get targetTemperature() {
        if (thermostat.selectedTemperature > this._max) {
            return this._max;
        }
        else if (thermostat.selectedTemperature < this._min) {
            return this._min;
        }
        else {
            return thermostat.selectedTemperature;
        }
    }
}

if (thePlan.targetTemperature > thermostat.currentTemperature) {
    setToHeat();
}
else if (thePlan.targetTemperature < thermostat.currentTemperature) {
    setToCool();
}
else {
    setOff();
}
```

to

```javascript
class HeatingPlan {
    targetTemperature(selectedTemperature) {
        if (selectedTemperature > this._max) {
            return this._max;
        }
        else if (selectedTemperature < this._min) {
            return this._min;
        }
        else {
            return selectedTemperature;
        }
    }
}

if (thePlan.targetTemperature(thermostat.selectedTemperature) > thermostat.currentTemperature) {
    setToHeat();
}
else if (thePlan.targetTemperature(thermostat.selectedTemperature) < thermostat.currentTemperature) {
    setToCool();
}
else {
    setOff();
}
```



### 6.7 移除Setting方法（Remove Setting Method）

**动机**

1. 移除Setting方法可以使得对象变成无状态的，从而减少了修改对象来带的边际效应；

From

```javascript
class Person {
    get name() { return this._name; }
    set name(arg) { this._name = arg; }
    get id() { return this._id; }
    set id(arg) { this._id = arg; }
}

const martin = new Person();
martin.name = "martin";
martin.id = "1234";
```

to

```javascript
class Person {
    constructor(id) {
        this._id = id;
    }
    get name() { return this._name; }
    set name(arg) { this._name = arg; }
    get id() { return this._id; }
}

const martin = new Person("1234");
martin.name = "martin";
```



### 6.8 使用工厂方法替代构造方法（Replace Constructor With Factory)

**动机**

1. 工厂方法没有命名限制，也没有返回类型限制，比构造方法更加灵活、易用；

From

```javascript
class Employee {
    constructor(name, typeCode) {
        this._name = name;
        this._typeCode = typeCode;
    }
    get name() { return this._name; }
    get type() {
        return Employee.legalTypeCodes[this._typeCode];
    }
    static get legalTypeCodes() {
        return { "E": "Engineer", "M": "Manager", "S": "Salesman" };
    }
}

candidate = new Employee(document.name, document.empType);

const leadEngineer = new Employee(document.leadEngineer, 'E');
```

to

```javascript
class Employee {
    constructor(name, typeCode) {
        this._name = name;
        this._typeCode = typeCode;
    }
    get name() { return this._name; }
    get type() {
        return Employee.legalTypeCodes[this._typeCode];
    }
    static get legalTypeCodes() {
        return { "E": "Engineer", "M": "Manager", "S": "Salesman" };
    }
}

function createEmployee(name, typeCode) {
    return new Employee(name, typeCode);
}

candidate = createEmployee(document.name, document.empType);

const leadEngineer = createEmployee(document.leadEngineer, 'E');
```



### 6.9 使用命令对象替代函数（Replace Function With Command）

**动机**

1. 命令对象的功能比函数更加丰富，使用更加灵活；
2. 使用命令对象可以将复杂函数进行细分，并且充分利用面向对象的特性；

From

```javascript
function score(candidate, medicalExam, scoringGuide) {
    let result = 0;
    let healthLevel = 0;
    let highMedicalRiskFlag = false;
    if (medicalExam.isSmoker) {
        healthLevel += 10;
        highMedicalRiskFlag = true;
    }
    let certificationGrade = "regular";
    if (scoringGuide.stateWithLowCertification(candidate.originState)) {
        certificationGrade = "low";
        result -= 5;
    }
    // lots more code like this
    result -= Math.max(healthLevel - 5, 0);
    return result;
}
```

to

```javascript
function score(candidate, medicalExam, scoringGuide) {
    return new Scorer(candidate, medicalExam, scoringGuide).execute();
}

class Scorer {
    constructor(candidate, medicalExam, scoringGuide) {
        this._candidate = candidate;
        this._medicalExam = medicalExam;
        this._scoringGuide = scoringGuide;
    }

    execute() {
        this._result = 0;
        this._healthLevel = 0;
        this._highMedicalRiskFlag = false;
        this.scoreSmoking();
        this._certificationGrade = "regular";
        if (this._scoringGuide.stateWithLowCertification(this._candidate.originState)) {
            this._certificationGrade = "low";
            this._result -= 5;
        }
        // lots more code like this
        this._result -= Math.max(this._healthLevel - 5, 0);
        return this._result;
    }
    
    scoreSmoking() {
        if (this._medicalExam.isSmoker) {
            this._healthLevel += 10;
            this._highMedicalRiskFlag = true;
        }
    }
}
```



### 6.10 使用函数替代命令对象（Replace Command With Function）

**动机**

1. 如果函数逻辑本身较为简单，则函数比命令对象更容易维护；

From

```javascript
class ChargeCalculator {
    constructor(customer, usage) {
        this._customer = customer;
        this._usage = usage;
    }
    execute() {
        return this._customer.rate * this._usage;
    }
}
```

to

```javascript
function charge(customer, usage) {
    return customer.rate * usage;
}
```



## 7 处理继承



### 7.1 方法上移（Pull Up Method）

**动机**

1. 当子类拥有类似的方法，而父类没有时，将方法上移到父类以减少重复；

From

```javascript
class Employee extends Party {
    get annualCost() {
        return this.monthlyCost * 12;
    }
}
class Department extends Party {
    get totalAnnualCost() {
        return this.monthlyCost * 12;
    }
}
```

to

```javascript
class Party {
    get annualCost() {
        return this.monthlyCost * 12;
    }
    get monthlyCost() {
        throw new SubclassResponsibilityError();
    }
}
```



### 7.2 字段上移（Pull Up Field）

**动机**

1. 当子类有类似的字段，而父类没有时，将字段上移到父类以减少重复；

From

```java
class Employee {...} // Java
class Salesman extends Employee {
      private String name;
}
class Engineer extends Employee {
      private String name;
}
```

to

```java
class Employee {
      protected String name;
}
class Salesman extends Employee {...}
class Engineer extends Employee {...}
```



### 7.3 构造方法上移（Pull Up Constructor Body）

**动机**

1. 当子类的构造方法中有类似行为，而父类没有时，将构造方法内容上移到父类构造方法中以减少重复；

From

```javascript
class Party { }
class Employee extends Party {
    constructor(name, id, monthlyCost) {
        super();
        this._id = id;
        this._name = name;
        this._monthlyCost = monthlyCost;
    }
}
class Department extends Party {
    constructor(name, staff) {
        super();
        this._name = name;
        this._staff = staff;
    }
}
```

to

```javascript
class Party {
    constructor(name) {
        this._name = name;
    }
}
class Employee {
    constructor(name, id, monthlyCost) {
        super(name);
        this._id = id;
        this._monthlyCost = monthlyCost;
    }
}
class Department {
    constructor(name, staff) {
        super(name);
        this._staff = staff;
    }
}
```



### 7.4 方法下沉（Push Down Method）

**动机**

1. 如果父类中的方法只被其中一个子类使用，则应该将方法下沉到子类中；

From

```javascript
class Employee {
    get quota {... }
}
class Engineer extends Employee {... }
class Salesman extends Employee {... }
```

to

```javascript
class Employee {... }
class Engineer extends Employee {... }
class Salesman extends Employee {
    get quota {... }
}
```



### 7.5 字段下沉（Push Down Field）

**动机**

1. 如果父类中的字段只被其中一个子类使用，则应该将字段下沉到子类中；

From

```java
class Employee { // Java
      private String quota;
}
class Engineer extends Employee {...}
class Salesman extends Employee {...}
```

to

```java
class Employee {...}
class Engineer extends Employee {...}
class Salesman extends Employee {
protected String quota;
}
```



### 7.6 使用子类替代类型编码（Replace Type Code With Subclasses）

**动机**

1. 将同一种对象的不同类型变化转变为不同的子类型，以便利用面向对象的特性；

From

```javascript
class Employee {
    constructor(name, type) {
        this.validateType(type);
        this._name = name;
        this._type = type;
    }
    validateType(arg) {
        if (!["engineer", "manager", "salesman"].includes(arg))
            throw new Error(`Employee cannot be of type ${arg}`);
    }
    toString() { return `${this._name} (${this._type})`; }
}
```

to

```javascript
class Employee {
    constructor(name) {
        this._name = name;
    }
    toString() { return `${this._name} (${this.type})`; }
}

class Engineer extends Employee {
    get type() { return "engineer"; }
}

class Salesman extends Employee {
    get type() { return "salesman"; }
}

class Manager extends Employee {
    get type() { return "manager"; }
}

function createEmployee(name, type) {
    switch (type) {
        case "engineer": return new Engineer(name, type);
        case "salesman": return new Salesman(name, type);
        case "manager": return new Manager(name, type);
    }
    return new Employee(name, type);
}
```



### 7.7 移除子类

**动机**

1. 如果子类的功能太少，以至于逐渐失去存在的价值，则可以使用类型编码替代子类；

From

```javascript
class Person {
    constructor(name) {
        this._name = name;
    }
    get name() { return this._name; }
    get genderCode() { return "X"; }
}
class Male extends Person {
    get genderCode() { return "M"; }
}
class Female extends Person {
    get genderCode() { return "F"; }
}
```

to

```javascript
class Person {
    constructor(name, genderCode) {
        this._name = name;
        this._genderCode = genderCode;
    }
}
```



### 7.8 提取抽象类（Extract Superclass）

**动机**

1. 如果两个类的功能相似，则考虑提取抽象类，以便消除重复，利用面向对象的特性；

From

```javascript
class Department {
   get totalAnnualCost() {...}
   get name() {...}
   get headCount() {...}
}
class Employee {
   get annualCost() {...}
   get name() {...}
   get id() {...}
}
```

to

```javascript
class Party {
    get name() {... }
    get annualCost() {... }
}
class Department extends Party {
    get annualCost() {... }
    get headCount() {... }
}
class Employee extends Party {
    get annualCost() {... }
    get id() {... }
}
```



### 7.9 层级合并（Collapse Hierarchy）

**动机**

1. 如果子类与父类逐渐变得相同，则考虑将子类的功能合并到父类；

From

```javascript
class Employee {...}
class Salesman extends Employee {...}
```

to

```javascript
class Employee {...}
```



### 7.10 使用代理替代子类（Replace Subclass With Delegate）

**动机**

1. 类的复合优于继承，因为继承带来了强约束，父类的变化很容易影响子类的功能，通过代理可以保持一种松散的关系；

From

```javascript
class Order {
    get daysToShip() {
        return this._warehouse.daysToShip;
    }
}
class PriorityOrder extends Order {
    get daysToShip() {
        return this._priorityPlan.daysToShip;
    }
}

```

to

```javascript
class Order {
    get daysToShip() {
        return (this._priorityDelegate)
            ? this._priorityDelegate.daysToShip
            : this._warehouse.daysToShip;
    }
}
class PriorityOrderDelegate {
    get daysToShip() {
        return this._priorityPlan.daysToShip
    }
}
```



### 7.11 使用代理替代父类（Replace Superclass With Delegate）

**动机**

1. 类的复合优于继承，因为继承带来了强约束，父类的变化很容易影响子类的功能，通过代理可以保持一种松散的关系；

From

```javascript
class List {...}
class Stack extends List {...}
```

to

```javascript
class Stack {
    constructor() {
        this._storage = new List();
    }
}
class List {... }
```
