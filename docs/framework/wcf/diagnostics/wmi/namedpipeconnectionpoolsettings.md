---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8422e1adf9a8914b631431eba5c9c0ed058cd0f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258025"
---
# <a name="namedpipeconnectionpoolsettings"></a>NamedPipeConnectionPoolSettings

NamedPipeConnectionPoolSettings  
  
## <a name="syntax"></a>구문  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>메서드  

 NamedPipeConnectionPoolSettings 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  

 NamedPipeConnectionPoolSettings 클래스에는 다음과 같은 속성이 있습니다.  
  
### <a name="groupname"></a>GroupName  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 바인딩 요소가 사용하는 연결 풀의 그룹 이름입니다.  
  
### <a name="idletimeout"></a>IdleTimeout  

 데이터 형식: datetime  
  
 액세스 형식: 읽기 전용  
  
 연결이 끊어지기 전에 유휴 상태일 수 있는 최대 시간입니다.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  

 데이터 형식: sint32  
  
 액세스 형식: 읽기 전용  
  
 클라이언트에서 각 엔드포인트에 대한 최대 아웃바운드 연결 수입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
