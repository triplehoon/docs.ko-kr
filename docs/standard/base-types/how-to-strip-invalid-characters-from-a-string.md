---
title: '방법: 문자열에서 유효하지 않은 문자 제거'
description: 정적 Regex.Replace 메서드를 사용하여 문자열에서 잠재적으로 유해한 문자를 제거하는 방법을 보여 주는 예제를 참조하세요.
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET regular expressions, examples
- regular expressions [.NET], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
ms.openlocfilehash: d6422556ab9c7d2100ea66e6b0dae1ee01e0e434
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683851"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>방법: 문자열에서 유효하지 않은 문자 제거

다음 예제에서는 정적 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 메서드를 사용하여 문자열에서 잘못된 문자를 제거합니다.  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a>예제  

 이 예제에 정의된 `CleanInput` 메서드가 사용하여 사용자 입력을 허용하는 텍스트 필드에 입력한 문제가 될 수 있는 문자를 제거할 수 있습니다. 이 경우에 `CleanInput`은 마침표(.), 기호 (@), 하이픈(-)을 제외한 모든 영숫자가 아닌 문자를 제거하고 나머지 문자열을 반환합니다. 그러나 입력 문자열에 포함되어야 하는 모든 문자를 제거하도록 정규식 패턴을 수정할 수 있습니다.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 정규식 패턴 `[^\w\.@-]`은 단어 문자, 마침표, @ 기호 또는 하이픈이 아닌 모든 문자를 찾습니다. 단어 문자는 문자, 숫자 또는 밑줄과 같은 문장 부호입니다. 이 패턴과 일치하는 모든 문자는 바꾸기 패턴에 정의된 <xref:System.String.Empty?displayProperty=nameWithType> 문자열로 바뀝니다. 사용자 입력에서 추가 문자를 허용하려면 해당 문자를 정규식 패턴의 문자 클래스에 추가합니다. 예를 들어 정규식 패턴 `[^\w\.@-\\%]`도 입력 문자열에 백분율 기호 및 백슬래시를 허용합니다.  
  
## <a name="see-also"></a>참조

- [.NET 정규식](regular-expressions.md)
