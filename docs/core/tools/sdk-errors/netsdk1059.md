---
title: 'NETSDK1059: 프로젝트에 사용되지 않는 .NET CLI 도구가 포함되어 있음'
description: 프로젝트에 사용되지 않는 .NET CLI 도구가 포함되어 있는 문제를 해결하는 방법입니다.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1059
ms.openlocfilehash: b80f42495e1aff8d37008946f10f68c195d5a9ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713121"
---
# <a name="netsdk1059-project-contains-obsolete-net-cli-tool"></a>NETSDK1059: 프로젝트에 사용되지 않는 .NET CLI 도구가 포함되어 있음

**이 문서의 적용 대상:** ✔️ .NET Core 2.1.100 SDK 이상 버전

.NET SDK가 NETSDK1059 경고를 실행하는 경우 프로젝트에 사용되지 않는 .NET CLI 도구가 포함되어 있는 것입니다. .NET Core 2.1부터는 이러한 도구가 .NET SDK에 포함되며 프로젝트에서 명시적으로 참조할 필요가 없습니다. .NET Core 2.1로 마이그레이션하는 방법에 대한 자세한 내용은 [여기](https://aka.ms/dotnetclitools-in-box)에서 확인할 수 있습니다.
