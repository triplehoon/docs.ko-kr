---
title: 람다 식 - C# 참조
description: 람다 식에 대해 알아봅니다. 식이 본문으로 포함된 식 람다 또는 문 블록이 본문으로 포함된 문 람다가 있습니다.
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 3dd793ec000999935bff6b54b1b00e49211bd5ec
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558363"
---
# <a name="lambda-expressions-c-reference"></a><span data-ttu-id="90c20-104">람다 식(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="90c20-104">Lambda expressions (C# reference)</span></span>

<span data-ttu-id="90c20-105">*람다 식*은 다음 두 형식의 식입니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-105">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="90c20-106">식이 본문으로 포함된 [식 람다](#expression-lambdas):</span><span class="sxs-lookup"><span data-stu-id="90c20-106">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="90c20-107">문 블록이 본문으로 포함된 [문 람다](#statement-lambdas):</span><span class="sxs-lookup"><span data-stu-id="90c20-107">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="90c20-108">[람다 선언 연산자`=>`](lambda-operator.md)를 사용하여 본문에서 람다의 매개 변수 목록을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-108">Use the [lambda declaration operator `=>`](lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="90c20-109">람다 식을 만들려면 람다 연산자 왼쪽에 입력 매개 변수를 지정하고(있는 경우) 다른 쪽에 식이나 문 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-109">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="90c20-110">람다 식은 [대리자](../builtin-types/reference-types.md#the-delegate-type) 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-110">Any lambda expression can be converted to a [delegate](../builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="90c20-111">람다 식을 변환할 수 있는 대리자 형식은 해당 매개 변수 및 반환 값의 형식에 따라 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-111">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="90c20-112">람다 식에서 값을 반환하지 않는 경우 `Action` 대리자 형식 중 하나로 변환할 수 있습니다. 값을 반환하는 경우 `Func` 대리자 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-112">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="90c20-113">예를 들어 매개 변수는 두 개지만 값을 반환하지 않는 람다 식은 <xref:System.Action%602> 대리자로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-113">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="90c20-114">매개 변수가 하나이고 값을 반환하는 람다 식은 <xref:System.Func%602> 대리자로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-114">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="90c20-115">다음 예제에서는 `x`라고 이름이 지정되고 `x` 제곱 값을 반환하는 매개 변수를 지정하는 람다 식 `x => x * x`는 대리자 형식의 변수에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-115">In the following example, the lambda expression `x => x * x`, which specifies a parameter that's named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="90c20-116">다음 예제에 표시된 대로 식 람다는 [식 트리](../../programming-guide/concepts/expression-trees/index.md) 형식으로 변환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-116">Expression lambdas can also be converted to the [expression tree](../../programming-guide/concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="90c20-117">대리자 형식이나 식 트리의 인스턴스가 필요한 코드에서 람다 식을 백그라운드에서 실행해야 하는 코드를 전달하는 <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> 메서드의 인수 등으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-117">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="90c20-118">다음 예제에 표시된 대로 [C#에 LINQ](../../linq/index.md)를 작성할 때 람다 식을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-118">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="90c20-119">예를 들어 LINQ to Objects 및 LINQ to XML에서 메서드 기반 구문을 사용하여 <xref:System.Linq.Enumerable?displayProperty=nameWithType> 클래스에서 <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> 메서드를 호출하는 경우 매개 변수는 대리자 형식 <xref:System.Func%602?displayProperty=nameWithType>입니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-119">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="90c20-120">예를 들어 LINQ to SQL에서 <xref:System.Linq.Queryable?displayProperty=nameWithType> 클래스에서 <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> 메서드를 호출하는 경우 매개 변수 형식은 식 트리 형식 [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)입니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-120">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="90c20-121">두 경우 모두 동일한 람다 식을 사용하여 매개 변수 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-121">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="90c20-122">그러면 두 `Select` 호출이 비슷하게 보일 수 있지만 실제로 람다 식을 통해 생성되는 개체 형식은 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-122">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="90c20-123">식 람다</span><span class="sxs-lookup"><span data-stu-id="90c20-123">Expression lambdas</span></span>

<span data-ttu-id="90c20-124">`=>` 연산자의 오른쪽에 식이 있는 람다 식을 식 람다라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-124">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="90c20-125">식 람다는 [식 트리](../../programming-guide/concepts/expression-trees/index.md)를 만드는 데 광범위하게 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-125">Expression lambdas are used extensively in the construction of [expression trees](../../programming-guide/concepts/expression-trees/index.md).</span></span> <span data-ttu-id="90c20-126">식 람다는 식의 결과를 반환하며 기본 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="90c20-127">괄호는 람다 식에 입력 매개 변수가 하나뿐인 경우에만 생략할 수 있고 그렇지 않으면 생략할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="90c20-128">입력 매개 변수가 0개이면 다음과 같이 빈 괄호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-128">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="90c20-129">둘 이상의 입력 매개 변수는 다음과 같이 괄호로 묶고 쉼표로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-129">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="90c20-130">컴파일러에서 입력 형식을 유추할 수 없는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-130">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="90c20-131">다음 예제와 같이 형식을 명시적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-131">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="90c20-132">입력 매개 변수 형식은 모두 명시적이거나 암시적이어야 합니다. 그렇지 않으면 [CS0748](../../misc/cs0748.md) 컴파일러 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-132">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="90c20-133">식 람다의 본문은 메서드 호출로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-133">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="90c20-134">하지만 SQL Server와 같은 .NET 공용 언어 런타임의 컨텍스트 외부에서 평가되는 식 트리를 만드는 경우에는 람다 식에 메서드 호출을 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-134">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="90c20-135">이러한 메서드는 .NET 공용 언어 런타임의 컨텍스트 안에서만 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-135">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="90c20-136">문 람다</span><span class="sxs-lookup"><span data-stu-id="90c20-136">Statement lambdas</span></span>

<span data-ttu-id="90c20-137">문 람다는 다음과 같이 중괄호 안에 문을 지정한다는 점을 제외하면 식 람다와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-137">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="90c20-138">문 람다의 본문에 지정할 수 있는 문의 개수에는 제한이 없지만 일반적으로 2-3개 정도만 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="90c20-139">문 람다는 식 트리를 만드는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-139">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="90c20-140">비동기 람다</span><span class="sxs-lookup"><span data-stu-id="90c20-140">Async lambdas</span></span>

<span data-ttu-id="90c20-141">[async](../keywords/async.md) 및 [await](await.md) 키워드를 사용하여 비동기 처리를 통합하는 람다 식과 문을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../keywords/async.md) and [await](await.md) keywords.</span></span> <span data-ttu-id="90c20-142">예를 들어 다음 Windows Forms 예제에는 비동기 메서드 `ExampleMethodAsync`를 호출하고 기다리는 이벤트 처리기가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="90c20-143">비동기 람다를 사용하여 동일한 이벤트 처리기를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="90c20-144">이 처리기를 추가하려면 다음 예제에 표시된 것처럼 람다 매개 변수 목록에 `async` 한정자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="90c20-145">비동기 메서드를 만들고 사용하는 방법에 대한 자세한 내용은 [Async 및 Await를 사용한 비동기 프로그래밍](../../programming-guide/concepts/async/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90c20-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="90c20-146">람다 식 및 튜플</span><span class="sxs-lookup"><span data-stu-id="90c20-146">Lambda expressions and tuples</span></span>

<span data-ttu-id="90c20-147">C# 7.0부터 C# 언어에서 [튜플](../builtin-types/value-tuples.md)을 기본적으로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-147">Starting with C# 7.0, the C# language provides built-in support for [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="90c20-148">람다 식에 인수로 튜플을 제공할 수 있으며 람다 식에서 튜플을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-148">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="90c20-149">경우에 따라 C# 컴파일러는 형식 유추를 사용하여 튜플 구성 요소의 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-149">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="90c20-150">쉼표로 구분된 해당 구성 요소 목록을 괄호로 묶어 튜플을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-150">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="90c20-151">다음 예제에서는 3개 구성 요소가 있는 튜플을 사용하여 숫자 시퀀스를 람다 식에 전달하고 각 값을 두 배로 늘린 후 곱하기의 결과가 포함된, 3개 구성 요소가 있는 튜플을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-151">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="90c20-152">일반적으로 튜플 필드의 이름은 `Item1`, `Item2` 등입니다. 그러나 다음 예제에서처럼 명명된 구성 요소가 있는 튜플을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-152">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="90c20-153">C# 튜플에 관한 자세한 내용은 [튜플 형식](../../language-reference/builtin-types/value-tuples.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90c20-153">For more information about C# tuples, see [Tuple types](../../language-reference/builtin-types/value-tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="90c20-154">표준 쿼리 연산자와 람다 식</span><span class="sxs-lookup"><span data-stu-id="90c20-154">Lambdas with the standard query operators</span></span>

<span data-ttu-id="90c20-155">다른 구현 중에 LINQ to Objects는 형식이 제네릭 대리자의 <xref:System.Func%601> 패밀리 중 하나인 입력 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-155">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="90c20-156">이러한 대리자는 형식 매개 변수를 사용하여 입력 매개 변수의 수와 형식 및 대리자의 반환 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-156">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="90c20-157">`Func` 대리자는 소스 데이터 집합에 있는 각 요소에 적용할 사용자 정의 식을 캡슐화하는 데 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-157">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="90c20-158">예를 들어 <xref:System.Func%602> 대리자 형식을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-158">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="90c20-159">이 경우 대리자를 `Func<int, bool>` 인스턴스로 인스턴스화할 수 있습니다. 여기서 `int`는 입력 매개 변수이고, `bool`은 반환 값입니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-159">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="90c20-160">반환 값은 항상 마지막 형식 매개 변수에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-160">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="90c20-161">예를 들어 `Func<int, string, bool>`은 두 입력 매개 변수 `int` 및 `string`과 반환 형식 `bool`을 사용하여 대리자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-161">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="90c20-162">다음 `Func` 대리자를 호출하면 입력 매개 변수가 5인지 여부를 나타내는 부울 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-162">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="90c20-163"><xref:System.Linq.Queryable> 형식에 정의되어 있는 표준 쿼리 연산자의 경우와 같이 인수 형식이 <xref:System.Linq.Expressions.Expression%601>인 경우에도 람다 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-163">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="90c20-164"><xref:System.Linq.Expressions.Expression%601> 인수를 지정하면 람다 식이 식 트리로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-164">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="90c20-165">이 예제에서는 <xref:System.Linq.Enumerable.Count%2A> 표준 쿼리 연산자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-165">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="90c20-166">컴파일러에서 입력 매개 변수의 형식을 유추하거나 사용자가 형식을 명시적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-166">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="90c20-167">이 람다 식은 2로 나누었을 때 나머지가 1인 정수(`n`)의 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-167">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="90c20-168">다음 예제에서는 숫자 시퀀스에서 조건을 만족하지 않는 첫 번째 숫자가 9이기 때문에 `numbers` 배열에서 9 앞에 오는 모든 요소가 포함된 시퀀스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-168">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="90c20-169">다음 예제에서는 입력 매개 변수를 괄호로 묶어 여러 개 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-169">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="90c20-170">이 메서드는 값이 배열의 서수 위치보다 작은 숫자가 나타날 때까지 `numbers` 배열의 모든 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-170">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="90c20-171">람다 식에서의 형식 유추</span><span class="sxs-lookup"><span data-stu-id="90c20-171">Type inference in lambda expressions</span></span>

<span data-ttu-id="90c20-172">컴파일러에서는 람다 식 본문, 매개 변수 형식 및 C# 언어 사양에 설명되어 있는 기타 요소를 기준으로 형식을 유추할 수 있기 때문에 대부분의 경우에는 람다 식을 작성할 때 입력 매개 변수의 형식을 지정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-172">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="90c20-173">대부분의 표준 쿼리 연산자에서 첫 번째 입력 형식은 소스 시퀀스 요소의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-173">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="90c20-174">`IEnumerable<Customer>`를 쿼리할 경우 입력 변수가 `Customer` 개체로 유추됩니다. 이는 이 개체의 메서드와 속성에 액세스할 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-174">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="90c20-175">람다 식의 형식 유추에 대한 일반적인 규칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-175">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="90c20-176">람다 식과 대리자 형식에 포함된 매개 변수 수가 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-176">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="90c20-177">람다 식의 각 입력 매개 변수는 해당되는 대리자 매개 변수로 암시적으로 변환될 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-177">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="90c20-178">람다 식의 반환 값(있는 경우)은 대리자의 반환 형식으로 암시적으로 변환될 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-178">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="90c20-179">공용 형식 시스템에는 “람다 식”이라는 개념이 기본적으로 포함되어 있지 않기 때문에 람다 식 자체에는 형식이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-179">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="90c20-180">그러나 람다 식의 “형식”을 비공식적으로 언급해야 할 경우도 있는데</span><span class="sxs-lookup"><span data-stu-id="90c20-180">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="90c20-181">이 경우 형식은 대리자 형식 또는 람다 식이 변환되는 <xref:System.Linq.Expressions.Expression> 형식을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-181">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="90c20-182">람다 식에서 외부 변수 및 변수 범위 캡처</span><span class="sxs-lookup"><span data-stu-id="90c20-182">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="90c20-183">람다는 *외부 변수*를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-183">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="90c20-184">이러한 변수는 람다 식을 정의하는 메서드 범위 내에 있거나 람다 식을 포함하는 형식 범위 내에 있는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-184">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="90c20-185">이러한 방식으로 캡처되는 변수는 변수가 범위를 벗어나 가비지 수집되는 경우에도 람다 식에 사용할 수 있도록 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-185">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="90c20-186">외부 변수는 명확하게 할당해야만 람다 식에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-186">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="90c20-187">다음 예제에서는 이러한 규칙을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-187">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="90c20-188">람다 식의 변수 범위에는 다음과 같은 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-188">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="90c20-189">캡처된 변수는 해당 변수를 참조하는 대리자가 가비지 수집 대상이 될 때까지 가비지 수집되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-189">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="90c20-190">람다 식에 사용된 변수는 바깥쪽 메서드에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-190">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="90c20-191">람다 식은 바깥쪽 메서드에서 [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md) 또는 [out](../keywords/out-parameter-modifier.md) 매개 변수를 직접 캡처할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-191">A lambda expression cannot directly capture an [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md), or [out](../keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="90c20-192">람다 식의 [return](../keywords/return.md) 문에 의해서는 바깥쪽 메서드가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-192">A [return](../keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="90c20-193">해당 점프 문의 대상이 람다 식 블록을 벗어나는 경우 람다 식에는 [goto](../keywords/goto.md), [break](../keywords/break.md) 또는 [continue](../keywords/continue.md) 문을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-193">A lambda expression cannot contain a [goto](../keywords/goto.md), [break](../keywords/break.md), or [continue](../keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="90c20-194">대상이 블록 내에 있는 경우 람다 식 블록 외부에 점프 문을 사용해도 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="90c20-194">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="90c20-195">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="90c20-195">C# language specification</span></span>

<span data-ttu-id="90c20-196">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [익명 함수 식](~/_csharplang/spec/expressions.md#anonymous-function-expressions) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90c20-196">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="90c20-197">중요 설명서 장</span><span class="sxs-lookup"><span data-stu-id="90c20-197">Featured book chapter</span></span>

<span data-ttu-id="90c20-198">[대리자, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) 에 [ C# 3.0 Cookbook, Third Edition: 250 개 이상의 솔루션에 대 한 C# 3.0 프로그래머](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="90c20-198">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c20-199">참조</span><span class="sxs-lookup"><span data-stu-id="90c20-199">See also</span></span>

- [<span data-ttu-id="90c20-200">C# 참조</span><span class="sxs-lookup"><span data-stu-id="90c20-200">C# reference</span></span>](../index.md)
- [<span data-ttu-id="90c20-201">C# 연산자 및 식</span><span class="sxs-lookup"><span data-stu-id="90c20-201">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="90c20-202">LINQ(Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="90c20-202">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="90c20-203">식 트리</span><span class="sxs-lookup"><span data-stu-id="90c20-203">Expression Trees</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="90c20-204">로컬 함수 및 람다 식</span><span class="sxs-lookup"><span data-stu-id="90c20-204">Local functions vs. lambda expressions</span></span>](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="90c20-205">Visual Studio 2008 C# 샘플(LINQ 샘플 쿼리 파일 및 XQuery 프로그램 참조)</span><span class="sxs-lookup"><span data-stu-id="90c20-205">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)