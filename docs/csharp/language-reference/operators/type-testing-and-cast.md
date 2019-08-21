---
title: 类型测试和强制转换运算符 - C# 引用
description: 了解可用于检查表达式结果的类型并根据需要将其转换为另一种类型的 C# 运算符。
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: 6966d0b7a4f8a96bddb17ce2017fd53fc07ae922
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2019
ms.locfileid: "69572311"
---
# <a name="type-testing-and-cast-operators-c-reference"></a><span data-ttu-id="760fd-103">类型测试和强制转换运算符（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="760fd-103">Type-testing and cast operators (C# reference)</span></span>

<span data-ttu-id="760fd-104">可以使用以下运算符来执行类型检查或类型转换：</span><span class="sxs-lookup"><span data-stu-id="760fd-104">You can use the following operators to perform type checking or type conversion:</span></span>

- <span data-ttu-id="760fd-105">[is 运算符](#is-operator)：用于检查表达式的运行时类型是否与给定类型兼容</span><span class="sxs-lookup"><span data-stu-id="760fd-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="760fd-106">[as 运算符](#as-operator)：用于将表达式显式转换为给定类型（如果其运行时类型与该类型兼容）</span><span class="sxs-lookup"><span data-stu-id="760fd-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="760fd-107">[强制转换运算符 ()](#cast-operator-)：用于执行显式转换</span><span class="sxs-lookup"><span data-stu-id="760fd-107">[cast operator ()](#cast-operator-): to perform an explicit conversion</span></span>
- <span data-ttu-id="760fd-108">[typeof 运算符](#typeof-operator)：用于获取某个类型的 <xref:System.Type?displayProperty=nameWithType> 实例</span><span class="sxs-lookup"><span data-stu-id="760fd-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="760fd-109">is 运算符</span><span class="sxs-lookup"><span data-stu-id="760fd-109">is operator</span></span>

<span data-ttu-id="760fd-110">`is` 运算符检查表达式结果的运行时类型是否与给定类型兼容。</span><span class="sxs-lookup"><span data-stu-id="760fd-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="760fd-111">从 C# 7.0 开始，`is` 运算符还对照某个模式测试表达式结果。</span><span class="sxs-lookup"><span data-stu-id="760fd-111">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="760fd-112">具有类型测试 `is` 运算符的表达式具有以下形式</span><span class="sxs-lookup"><span data-stu-id="760fd-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="760fd-113">其中 `E` 是返回一个值的表达式，`T` 是类型或类型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="760fd-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="760fd-114">`E` 不得为匿名方法或 Lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="760fd-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="760fd-115">如果 `E` 的结果为非 null 且可以通过引用转换、装箱转换或取消装箱转换来转换为类型 `T`，则 `E is T` 表达式将返回 `true`；否则，它将返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="760fd-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="760fd-116">`is` 运算符不会考虑用户定义的转换。</span><span class="sxs-lookup"><span data-stu-id="760fd-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="760fd-117">以下示例演示，如果表达式结果的运行时类型派生自给定类型，即类型之间存在引用转换，`is` 运算符将返回 `true`：</span><span class="sxs-lookup"><span data-stu-id="760fd-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="760fd-118">以下示例演示，`is` 运算符将考虑装箱和取消装箱转换，但不会考虑数值转换：</span><span class="sxs-lookup"><span data-stu-id="760fd-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider numeric conversions:</span></span>

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="760fd-119">有关 C# 转换的信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的[转换](~/_csharplang/spec/conversions.md)一章。</span><span class="sxs-lookup"><span data-stu-id="760fd-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="760fd-120">有模式匹配的类型测试</span><span class="sxs-lookup"><span data-stu-id="760fd-120">Type testing with pattern matching</span></span>

<span data-ttu-id="760fd-121">从 C# 7.0 开始，`is` 运算符还对照某个模式测试表达式结果。</span><span class="sxs-lookup"><span data-stu-id="760fd-121">Starting with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="760fd-122">具体而言，它支持以下形式的类型模式：</span><span class="sxs-lookup"><span data-stu-id="760fd-122">In particular, it supports the type pattern in the following form:</span></span>

```csharp
E is T v
```

<span data-ttu-id="760fd-123">其中，`E` 为返回值的表达式，`T` 为类型或类型参数的名称，`v` 为类型 `T` 的新局部变量。</span><span class="sxs-lookup"><span data-stu-id="760fd-123">where `E` is an expression that returns a value, `T` is the name of a type or a type parameter, and `v` is a new local variable of type `T`.</span></span> <span data-ttu-id="760fd-124">如果 `E` 的结果为非 null 且可以通过引用、装箱或取消装箱转换来转换为 `T`，则 `E is T v` 表达式将返回 `true`，`E` 结果转换后的值将分配给变量 `v`。</span><span class="sxs-lookup"><span data-stu-id="760fd-124">If the result of `E` is non-null and can be converted to `T` by a reference, boxing, or unboxing conversion, the `E is T v` expression returns `true` and the converted value of the result of `E` is assigned to variable `v`.</span></span>

<span data-ttu-id="760fd-125">以下示例演示了具有以下类型模式的 `is` 运算符的用法：</span><span class="sxs-lookup"><span data-stu-id="760fd-125">The following example demonstrates the usage of the `is` operator with the type pattern:</span></span>

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

<span data-ttu-id="760fd-126">有关类型模式和其他受支持模式的详细信息，请参阅[具有 is 的模式匹配](../keywords/is.md#pattern-matching-with-is)。</span><span class="sxs-lookup"><span data-stu-id="760fd-126">For more information about the type pattern and other supported patterns, see [Pattern matching with is](../keywords/is.md#pattern-matching-with-is).</span></span>

## <a name="as-operator"></a><span data-ttu-id="760fd-127">as 运算符</span><span class="sxs-lookup"><span data-stu-id="760fd-127">as operator</span></span>

<span data-ttu-id="760fd-128">`as` 运算符将表达式结果显式转换为给定的引用或可以为 null 值的类型。</span><span class="sxs-lookup"><span data-stu-id="760fd-128">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="760fd-129">如果无法进行转换，则 `as` 运算符返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="760fd-129">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="760fd-130">与[强制转换运算符 ()](#cast-operator-) 不同，`as` 运算符永远不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="760fd-130">Unlike the [cast operator ()](#cast-operator-), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="760fd-131">形式如下的表达式</span><span class="sxs-lookup"><span data-stu-id="760fd-131">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="760fd-132">其中，`E` 为返回值的表达式，`T` 为类型或类型参数的名称，生成相同的结果，</span><span class="sxs-lookup"><span data-stu-id="760fd-132">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="760fd-133">不同的是 `E` 只计算一次。</span><span class="sxs-lookup"><span data-stu-id="760fd-133">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="760fd-134">`as` 运算符仅考虑引用、可以为 null、装箱和取消装箱转换。</span><span class="sxs-lookup"><span data-stu-id="760fd-134">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="760fd-135">不能使用 `as` 运算符执行用户定义的转换。</span><span class="sxs-lookup"><span data-stu-id="760fd-135">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="760fd-136">若要执行此操作，请使用[强制转换运算符 ()](#cast-operator-)。</span><span class="sxs-lookup"><span data-stu-id="760fd-136">To do that, use the [cast operator ()](#cast-operator-).</span></span>

<span data-ttu-id="760fd-137">下面的示例演示 `as` 运算符的用法：</span><span class="sxs-lookup"><span data-stu-id="760fd-137">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="760fd-138">如之前的示例所示，你需要将 `as` 表达式的结果与 `null` 进行比较，以检查转换是否成功。</span><span class="sxs-lookup"><span data-stu-id="760fd-138">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="760fd-139">从 C# 7.0 开始，可以使用 [is 运算符](#type-testing-with-pattern-matching)测试转换是否成功，如果成功，则将其结果分配给新变量。</span><span class="sxs-lookup"><span data-stu-id="760fd-139">Starting with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-operator-"></a><span data-ttu-id="760fd-140">强制转换运算符 ()</span><span class="sxs-lookup"><span data-stu-id="760fd-140">Cast operator ()</span></span>

<span data-ttu-id="760fd-141">形式为 `(T)E` 的强制转换表达式将表达式 `E` 的结果显式转换为类型 `T`。</span><span class="sxs-lookup"><span data-stu-id="760fd-141">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="760fd-142">如果不存在从类型 `E` 到类型 `T` 的显式转换，则发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="760fd-142">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="760fd-143">在运行时，显式转换可能不会成功，强制转换表达式可能会引发异常。</span><span class="sxs-lookup"><span data-stu-id="760fd-143">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="760fd-144">下面的示例演示显式数值和引用转换：</span><span class="sxs-lookup"><span data-stu-id="760fd-144">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="760fd-145">有关支持的显式转换的信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的[显式转换](~/_csharplang/spec/conversions.md#explicit-conversions)部分。</span><span class="sxs-lookup"><span data-stu-id="760fd-145">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="760fd-146">有关如何定义自定义显式或隐式类型转换的信息，请参阅[用户定义转换运算符](user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="760fd-146">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="760fd-147">() 的其他用法</span><span class="sxs-lookup"><span data-stu-id="760fd-147">Other usages of ()</span></span>

<span data-ttu-id="760fd-148">你还可以使用括号[调用方法或调用委托](member-access-operators.md#invocation-operator-)。</span><span class="sxs-lookup"><span data-stu-id="760fd-148">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-operator-).</span></span>

<span data-ttu-id="760fd-149">括号的其他用法是指定表达式中计算操作的顺序。</span><span class="sxs-lookup"><span data-stu-id="760fd-149">Other use of parentheses is to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="760fd-150">有关详细信息，请参阅[运算符](../../programming-guide/statements-expressions-operators/operators.md)一文中的[添加括号](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses)部分。</span><span class="sxs-lookup"><span data-stu-id="760fd-150">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="760fd-151">对于按优先级排序的运算符列表，请参阅 [C# 运算符](index.md)。</span><span class="sxs-lookup"><span data-stu-id="760fd-151">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="760fd-152">TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="760fd-152">typeof operator</span></span>

<span data-ttu-id="760fd-153">`typeof` 运算符用于获取某个类型的 <xref:System.Type?displayProperty=nameWithType> 实例。</span><span class="sxs-lookup"><span data-stu-id="760fd-153">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="760fd-154">`typeof` 运算符的实参必须是类型或类型形参的名称，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="760fd-154">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="760fd-155">你还可以使用具有未绑定泛型类型的 `typeof` 运算符。</span><span class="sxs-lookup"><span data-stu-id="760fd-155">You also can use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="760fd-156">未绑定泛型类型的名称必须包含适当数量的逗号，且此数量小于类型参数的数量。</span><span class="sxs-lookup"><span data-stu-id="760fd-156">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="760fd-157">以下示例演示了具有未绑定泛型类型的 `typeof` 运算符的用法：</span><span class="sxs-lookup"><span data-stu-id="760fd-157">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="760fd-158">表达式不能为 `typeof` 运算符的参数。</span><span class="sxs-lookup"><span data-stu-id="760fd-158">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="760fd-159">若要获取表达式结果的运行时类型的 <xref:System.Type?displayProperty=nameWithType> 实例，请使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="760fd-159">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of the expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="760fd-160">使用 `typeof` 运算符进行类型测试</span><span class="sxs-lookup"><span data-stu-id="760fd-160">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="760fd-161">使用 `typeof` 运算符来检查表达式结果的运行时类型是否与给定的类型完全匹配。</span><span class="sxs-lookup"><span data-stu-id="760fd-161">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="760fd-162">以下示例演示了使用 `typeof` 运算符和 [is 运算符](#is-operator)执行的类型检查之间的差异：</span><span class="sxs-lookup"><span data-stu-id="760fd-162">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="760fd-163">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="760fd-163">Operator overloadability</span></span>

<span data-ttu-id="760fd-164">`is`、`as` 和 `typeof` 运算符不可重载。</span><span class="sxs-lookup"><span data-stu-id="760fd-164">The `is`, `as`, and `typeof` operators are not overloadable.</span></span>

<span data-ttu-id="760fd-165">用户定义的类型不能重载 `()` 运算符，但可以定义可由强制转换表达式执行的自定义类型转换。</span><span class="sxs-lookup"><span data-stu-id="760fd-165">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="760fd-166">有关详细信息，请参阅[用户定义转换运算符](user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="760fd-166">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="760fd-167">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="760fd-167">C# language specification</span></span>

<span data-ttu-id="760fd-168">有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：</span><span class="sxs-lookup"><span data-stu-id="760fd-168">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="760fd-169">is 运算符</span><span class="sxs-lookup"><span data-stu-id="760fd-169">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="760fd-170">as 运算符</span><span class="sxs-lookup"><span data-stu-id="760fd-170">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="760fd-171">强制转换表达式</span><span class="sxs-lookup"><span data-stu-id="760fd-171">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="760fd-172">typeof 运算符</span><span class="sxs-lookup"><span data-stu-id="760fd-172">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="760fd-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="760fd-173">See also</span></span>

- [<span data-ttu-id="760fd-174">C# 参考</span><span class="sxs-lookup"><span data-stu-id="760fd-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="760fd-175">C# 运算符</span><span class="sxs-lookup"><span data-stu-id="760fd-175">C# operators</span></span>](index.md)
- [<span data-ttu-id="760fd-176">操作说明：使用模式匹配以及 is 和 as 运算符安全地进行强制转换</span><span class="sxs-lookup"><span data-stu-id="760fd-176">How to: safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)