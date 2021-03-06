---
title: 类型设计准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 3e2fe7168bd0029d8f0e8f69a136c9089032973f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709018"
---
# <a name="type-design-guidelines"></a>类型设计准则
就 CLR 而言，它仅支持两种类型 — 引用类型和值类型。但出于探讨框架设计的目的，我们将类型划分为多个逻辑组，每种都有其特定的设计规则。  
  
 类是使用最普遍的引用类型。 多数框架中的大部分引用类型都是类。 类的广泛应用主要得益于其支持丰富的面向对象功能，以及普适性。 基类和抽象类是具备扩展性的特殊逻辑组。  
  
 接口也是一种类型。 接口可以被引用类型和值类型实现，因此可以充当这两种类型多态层次结构的根。 此外，接口也可用于模拟多个继承，而 CLR 本身并不支持该功能。  
  
 结构是常见的值类型。结构应当用来定义类似于语言基元的小型简单类型。  
  
 枚举是一种特殊的值类型，它适用于定义一组数量有限的值，例如一周七天的名称、控制台颜色等。  
  
 静态类的作用是为静态成员提供容器。 它们通常用来为其他操作提供快捷方式。  
  
 委托、异常、属性、数组和集合是适用于特定用途的特殊引用类型。关于这些类型的设计准则与使用情况将在本书其他章节中进行讨论。  
  
 **✓ DO** 确保每个类型定义完善的一组相关成员，而不仅仅是随机的不相关的功能集合。  
  
## <a name="in-this-section"></a>本节内容  
 [在类和结构之间选择](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [抽象类设计](../../../docs/standard/design-guidelines/abstract-class.md)  
 [静态类设计](../../../docs/standard/design-guidelines/static-class.md)  
 [接口设计](../../../docs/standard/design-guidelines/interface.md)  
 [结构设计](../../../docs/standard/design-guidelines/struct.md)  
 [枚举设计](../../../docs/standard/design-guidelines/enum.md)  
 [嵌套类型](../../../docs/standard/design-guidelines/nested-types.md)  
 *部分©2005，2009 Microsoft Corporation。保留所有权利。*  
  
 *在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。  
  
## <a name="see-also"></a>另请参阅

- [框架设计指南](../../../docs/standard/design-guidelines/index.md)
