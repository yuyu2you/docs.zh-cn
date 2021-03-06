---
title: 通用命名约定
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: d1b01fac7368ffeceb554c6f12aecb8f8760fa1d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709330"
---
# <a name="general-naming-conventions"></a>通用命名约定
本部分介绍与单词选择相关的一般命名约定、缩略词和首字母缩写词的使用准则以及有关如何避免使用特定于语言的名称的建议。  
  
## <a name="word-choice"></a>Word 选项  
 **✓ 务必**选择易读的标识符名称。  
  
 例如，在英语中，属性名称 `HorizontalAlignment` 比 `AlignmentHorizontal` 更具可读性。  
  
 **✓ DO** 可读性比简洁性更。  
  
 属性名称 `CanScrollHorizontally` 优于 `ScrollableX`（对 x 轴的指代显得模糊）。  
  
 **X 不要**使用下划线、连字符或任何其他非字母数字字符。  
  
 **X 不要**使用匈牙利表示法。  
  
 **X AVOID** 使用广泛与关键字冲突的标识符使用编程语言。  
  
 根据公共语言规范 (CLS) 规则 4，所有兼容语言均须提供一种机制，通过该机制能够访问将该语言的关键字用作标识符的命名项。 例如，C# 使用 @ 符号作为转义机制。 但是，仍然建议避免使用常用关键字，因为使用应用转义序列的方法比使用不应用转译序列的方法要困难得多。  
  
## <a name="using-abbreviations-and-acronyms"></a>使用缩写和首字母缩写  
 **X 不要**在标识符名称中使用缩写形式或缩略形式。  
  
 例如，使用 `GetWindow` 而不是 `GetWin`。  
  
 **X 不要**使用任何不常用的首字母缩写形式，即使是常用形式，也应只在必要时使用。  
  
## <a name="avoiding-language-specific-names"></a>避免特定于语言的名称  
 **✓ 务必**使用在语义上有意义的名称而不是特定于语言的关键字作为类型名称。  
  
 例如，`GetLength` 比 `GetInt` 更适合用作名称。  
  
 **✓ DO** 在极少数情况下在标识符的语义含义仅限于其类型中使用泛型的 CLR 类型名称，而不是使用语言特定的名称。  
  
 例如，转换为 <xref:System.Int64> 的方法应命名为 `ToInt64`，而不是 `ToLong`（因为 <xref:System.Int64> 是特定于 C# 的别名 `long` 的 CLR 名称）。 下表列出了几种使用 CLR 类型名称（以及 C#、Visual Basic 和 C++ 的对应类型名称）的基本数据类型。  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**Short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|unsigned __int64|**UInt64**|  
|**float**|**单精度**|**float**|**单精度**|  
|**双精度**|**双精度**|**双精度**|**双精度**|  
|**bool**|**布尔值**|**bool**|**布尔值**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**字符串**|**字符串**|**字符串**|  
|**object**|**对象**|**对象**|**对象**|  
  
 **✓ DO** 使用公用名，如`value`或`item`，而不是重复的类型名称，在极少数的情况下当的标识符具有任何语义含义和参数的类型并不重要。  
  
## <a name="naming-new-versions-of-existing-apis"></a>为现有 API 的新版本命名  
 **✓ 务必**在创建现有 API 的新版本时，使用与旧 API 类似的名称。  
  
 这有助于体现 API 之间的关系。  
  
 **✓ 务必**优先使用后缀而不是前缀来指示现有 API 的新版本。  
  
 这有助于在浏览文档或使用 IntelliSense 时更易发现所需内容。 旧版 API 的组织方式与新版 API 接近，因为大多数浏览器和 IntelliSense 都按字母顺序显示标识符。  
  
 **✓ 考虑**使用全新但有意义的标识符，而不是添加一个后缀或前缀。  
  
 **✓ 务必**使用数字后缀来指示现有 API 的新版本，特别是在 API 的现有名称是唯一有意义的名称（即该名称为行业标准）并且添加任何有意义的后缀（或更改其名称）都不合适的情况下。  
  
 **X 不要**使用 "Ex"（或类似）后缀作为区分同一 API 的早期版本和新版本的标识符。  
  
 **✓ 务必**在引入以 64 位整数（长整型）而非 32 位整数运行的 API 版本时，使用后缀 "64"。 只需在存在 32 位 API 时采用此方法；不要对只有 64 位版本的全新 API 应用此方法。  
  
 *部分©2005，2009 Microsoft Corporation。保留所有权利。*  
  
 *在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。  
  
## <a name="see-also"></a>另请参阅

- [框架设计指南](../../../docs/standard/design-guidelines/index.md)
- [命名规则](../../../docs/standard/design-guidelines/naming-guidelines.md)
