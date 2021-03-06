---
title: <routing>의 <filters>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855242"
---
# <a name="filters-of-routing"></a>\<routing>의 \<filters>

<xref:System.ServiceModel.Dispatcher.MessageFilter>들어오는 메시지를 평가할 때 사용할 WCF (Windows Communication Foundation 형식)를 결정 하는 라우팅 필터 집합을 정의 하기 위한 구성 섹션을 나타냅니다.

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소

다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

None

### <a name="child-elements"></a>자식 요소

|     | Description |
| --- | ----------- |
| [**\<filter>**](filter.md) | 들어오는 메시지를 평가할 때 사용할 WCF (Windows Communication Foundation 형식)를 결정 하는 라우팅 필터를 포함 <xref:System.ServiceModel.Dispatcher.MessageFilter> 합니다. |

### <a name="parent-elements"></a>부모 요소

|     | Description |
| --- | ----------- |
| [**\<routing>**](routing.md) | <xref:System.ServiceModel.Dispatcher.MessageFilter>들어오는 메시지를 평가할 때 사용할 WCF (Windows Communication Foundation 유형)와 필터가 일치할 때 메시지를 보낼 대상 끝점을 정의 하는 라우팅 테이블을 결정 하는 라우팅 필터 집합을 정의 하기 위한 구성 섹션을 나타냅니다. |

## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
