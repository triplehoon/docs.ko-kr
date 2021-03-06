---
title: 이식성 및 상호 운용성 규칙 (코드 분석)
description: 코드 분석 규칙 이식성 및 상호 운용성 규칙에 대해 알아보기
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592411"
---
# <a name="portability-and-interoperability-rules"></a>이식성 및 상호 운용성 규칙

이식성 규칙은 여러 플랫폼 간의 이식성을 지원 합니다. 상호 운용성 규칙은 COM 클라이언트와의 상호 작용을 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

| 규칙 | 설명 |
| - | - |
| [CA1401: P/Invoke는 노출 되지 않아야 합니다.](ca1401.md) | 공용 형식의 public 또는 protected 메서드에 System.Runtime.InteropServices.DllImportAttribute 특성이 있습니다 .이 특성은 Visual Basic의 Declare 키워드에 의해 구현 됩니다. 이러한 메서드는 노출되지 않아야 합니다. |
| [CA1416: 플랫폼 호환성 유효성 검사](ca1416.md) | 구성 요소에서 플랫폼 종속 Api를 사용 하면 모든 플랫폼에서 코드가 더 이상 작동 하지 않습니다. |
| [CA1417: `OutAttribute` P/invoke에 문자열 매개 변수를 사용 하지 마십시오.](ca1417.md) | 로 값으로 전달 되는 문자열 매개 변수는 `OutAttribute` 문자열이 인턴 문자열이 면 런타임을 불안정 하 게 만들 수 있습니다. |
