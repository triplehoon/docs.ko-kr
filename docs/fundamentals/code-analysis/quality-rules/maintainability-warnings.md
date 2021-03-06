---
title: 유지 관리 규칙 (코드 분석)
description: 코드 분석 유지 관리 규칙에 대해 알아봅니다.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592406"
---
# <a name="maintainability-rules"></a>유지 관리 규칙

유지 관리 규칙은 라이브러리 및 응용 프로그램 유지 관리를 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

| 규칙 | 설명 |
|-----------|-----------------------------------|
| [CA1501: 상속성을 너무 많이 사용하지 마세요.](ca1501.md) | 형식이 상속 계층 구조에서 네 단계보다 아래에 있습니다. 여러 번 중첩된 형식 계층 구조는 추적하고, 이해하고, 유지 관리하기가 어렵습니다. |
| [CA1502: 지나치게 복잡하게 만들지 마세요.](ca1502.md) | 이 규칙은 메서드를 통과하는 선형 독립 경로의 수를 측정하며 조건부 분기의 수와 복잡성에 의해 결정됩니다. |
| [CA1505: 유지 관리할 수 없는 코드를 사용하지 마세요.](ca1505.md) | 형식 또는 메서드에 낮은 유지 관리 인덱스 값이 있습니다. 낮은 유지 관리 인덱스는 형식 또는 메서드가 유지 관리하기 어렵고 다시 디자인될 수 있음을 나타냅니다. |
| [CA1506: 클래스를 지나치게 많이 결합하지 마세요.](ca1506.md) | 이 규칙은 형식 또는 메서드에 들어 있는 고유한 형식 참조의 개수를 계산하여 클래스 결합을 측정합니다. |
| [CA1507: 문자열 대신 nameof 사용](ca1507.md) | 문자열 리터럴은 식을 사용할 수 있는 인수로 사용 됩니다 `nameof` . |
| [CA1508: 데드 조건부 코드 방지](ca1508.md) | 메서드에는 항상 `true` 또는 런타임 시로 계산 되는 조건부 코드가 있습니다 `false` . 이렇게 하면 조건의 분기에서 데드 코드가 발생 `false` 합니다. |
| [CA1509: 코드 메트릭 구성 파일의 잘못된 항목](ca1509.md) | [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) 및 [CA1506](ca1506.md)와 같은 코드 메트릭 규칙에서 `CodeMetricsConfig.txt` 잘못 된 항목을 포함 하는 이라는 구성 파일을 제공 했습니다. |

## <a name="see-also"></a>참고 항목

- [관리 코드의 복잡성 및 유지 관리 용이성 측정](/visualstudio/code-quality/code-metrics-values)
