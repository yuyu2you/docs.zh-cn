---
title: 迭代器
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351520"
---
# <a name="iterator-visual-basic"></a>迭代器 (Visual Basic)
指定函数或 `Get` 访问器是迭代器。  
  
## <a name="remarks"></a>备注  
 *迭代器*对集合执行自定义迭代。 迭代器使用[Yield](../../../visual-basic/language-reference/statements/yield-statement.md)语句每次返回集合中的每个元素。 当到达 `Yield` 语句时，将保留代码中的当前位置。 下次调用迭代器函数时，将从该位置重新开始执行。  
  
 迭代器可作为函数或属性定义的 `Get` 访问器来实现。 `Iterator` 修饰符出现在迭代器函数的声明或 `Get` 访问器的声明中。  
  
 使用 For Each ... 将从客户端代码调用迭代器[下一语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
 迭代器函数或 `Get` 访问器的返回类型可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
 迭代器不能有任何 `ByRef` 参数。  
  
 不能在事件、实例构造函数、静态构造函数或静态析构函数中使用迭代器。  
  
 迭代器可以是匿名函数。 有关详细信息，请参阅[迭代器](../../programming-guide/concepts/iterators.md)。  
  
## <a name="usage"></a>用法  
 `Iterator` 修饰符可用于下面的上下文中：  
  
- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>示例  
 下面的示例演示迭代器函数。 迭代器函数的 `Yield` 语句位于[For 。下一个](../../../visual-basic/language-reference/statements/for-next-statement.md)循环。 `Main` 中[每](../../../visual-basic/language-reference/statements/for-each-next-statement.md)个语句体的每次迭代都会创建对 `Power` 迭代器函数的调用。 对迭代器函数的每个调用将继续到 `Yield` 语句的下一次执行（在 `For…Next` 循环的下一次迭代期间发生）。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>示例  
 下面的示例演示一个作为迭代器的 `Get` 访问器。 `Iterator` 修饰符位于属性声明中。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 有关其他示例，请参阅[迭代](../../programming-guide/concepts/iterators.md)器。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [迭代器](../../programming-guide/concepts/iterators.md)
- [Yield 语句](../../../visual-basic/language-reference/statements/yield-statement.md)
