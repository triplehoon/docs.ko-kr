---
title: raceOnRCWCleanup MDA
description: 다른 스레드에서 RCW를 사용 하거나 .NET의 스레드를 해제할 때 활성화 되는 raceOnRCWCleanup MDA (관리 디버깅 도우미)를 검토 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: 393c5ea44108445a9a1a9d16e7d1d192eced5740
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271449"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA

`raceOnRCWCleanup` MDA(관리 디버깅 도우미)는 CLR(공용 언어 런타임)에서 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> 메서드와 같은 명령을 사용하여 해제 호출을 수행할 때 RCW( [런타임 호출 가능 래퍼](../../standard/native-interop/runtime-callable-wrapper.md))가 사용 중임을 발견할 경우 활성화됩니다.  
  
## <a name="symptoms"></a>증상  

 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 또는 이와 비슷한 메서드를 사용하여 RCW를 해제하는 중이나 그 이후에 액세스 위반 또는 메모리 손상이 발생합니다.  
  
## <a name="cause"></a>원인  

 RCW가 다른 스레드나 해제 스레드 스택에서 사용 중입니다.  사용 중인 RCW는 해제할 수 없습니다.  
  
## <a name="resolution"></a>해결 방법  

 현재 스레드나 다른 스레드에서 사용 중일 수 있는 RCW는 해제하지 마세요.  
  
## <a name="effect-on-the-runtime"></a>런타임에 대한 영향  

 이 MDA는 CLR에 아무런 영향을 미치지 않습니다.  
  
## <a name="output"></a>출력  

 오류를 설명하는 메시지입니다.  
  
## <a name="configuration"></a>구성  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [관리 디버깅 도우미를 사용하여 오류 진단](diagnosing-errors-with-managed-debugging-assistants.md)
- [interop 마샬링](../interop/interop-marshaling.md)
