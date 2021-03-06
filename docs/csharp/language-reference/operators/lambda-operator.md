---
description: '>= 연산자 - C# 참조'
title: '>= 연산자 - C# 참조'
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 6a4df3a4bd358b87f98ff1bd5a3f624b1029a73b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128363"
---
# <a name="-operator-c-reference"></a>=> 연산자(C# 참조)

`=>` 토큰은 [람다 연산자](#lambda-operator)와 [식 본문 정의](#expression-body-definition)의 멤버 이름과 멤버 구현의 구분자라는 두 가지 형식으로 지원됩니다.

## <a name="lambda-operator"></a>람다 연산자

[람다 식](lambda-expressions.md)에서 람다 연산자 `=>`은 왼쪽의 입력 매개 변수를 오른쪽의 람다 본문과 구분합니다.

다음 예제에서는 메서드 구문이 포함된 [LINQ](../../programming-guide/concepts/linq/index.md) 기능을 사용하여 람다 식의 사용법을 보여줍니다.

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

람다 식의 입력 매개 변수는 컴파일 시 강력한 형식을 지정합니다. 위의 예제와 같이 컴파일러가 입력 매개 변수의 형식을 추론하는 경우, 형식 선언을 생략할 수 있습니다. 입력 매개 변수의 형식을 지정해야 하는 경우 다음 예제와 같이 각 매개 변수에 대해 입력매개 변수를 지정해야 합니다.

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

다음 예제에서는 입력 매개 변수 없이 람다 식을 정의하는 방법을 보여줍니다.

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

자세한 내용은 [람다 식](lambda-expressions.md)을 참조하세요.

## <a name="expression-body-definition"></a>식 본문 정의

식 본문 정의의 일반 구문은 다음과 같습니다.

```csharp
member => expression;
```

여기서 `expression`은(는) 유효한 식입니다. `expression`의 반환 형식은 구성원의 반환 형식으로 암시적으로 변환할 수 있어야 합니다. 멤버의 반환 형식이 `void`거나 구성원이 생성자, 종료자, 속성 또는 인덱서 `set` 접근자인 경우 `expression`은 [‘식 문’](~/_csharplang/spec/statements.md#expression-statements)이어야 합니다. 식의 결과는 삭제되므로 해당 식의 반환 형식은 어떤 형식도 될 수 있습니다.

다음 예제에서는 `Person.ToString` 메서드에 대한 식 본문 정의를 보여줍니다.

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

다음과 같은 메서드 정의의 약식 버전입니다.

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

메서드, 연산자 및 읽기 전용 속성에 대한 식 본문 정의는 C# 6부터 지원됩니다. 생성자, 종료자, 속성 및 인덱서 접근자에 대한 식 본문 정의는 C# 7.0부터 지원됩니다.

자세한 내용은 [식 본문 멤버](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)를 참조하세요.

## <a name="operator-overloadability"></a>연산자 오버로드 가능성

`=>` 연산자를 오버로드할 수 없습니다.

## <a name="c-language-specification"></a>C# 언어 사양

람다 연산자에 대한 자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [익명 함수 식](~/_csharplang/spec/expressions.md#anonymous-function-expressions) 섹션을 참조하세요.

## <a name="see-also"></a>참조

- [C# 참조](../index.md)
- [C# 연산자 및 식](index.md)
