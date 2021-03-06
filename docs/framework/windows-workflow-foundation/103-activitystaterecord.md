---
title: 103 - ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 02c33f02b7650c9f9b7527c319de3b58980fdd6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275078"
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord

## <a name="properties"></a>속성  
  
|||  
|-|-|  
|Id|103|  
|키워드|EndToEndMonitoring, 문제 해결, HealthMonitoring, WFTracking|  
|Level|정보|  
|채널|Microsoft-Windows-애플리케이션 서버-애플리케이션/분석|  
  
## <a name="description"></a>Description  

 워크플로 인스턴스 내의 활동에서 ActivityStateRecord를 내보내면 ETW 추적 참가자가 이 이벤트를 내보냅니다.  
  
## <a name="message"></a>메시지  

 TrackRecord = ActivityStateRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, State = %4, Name=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Arguments=%9, Variables=%10, Annotations=%11, ProfileName = %12  
  
## <a name="details"></a>세부 정보  
  
|데이터 항목 이름|데이터 항목 형식|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|워크플로의 인스턴스 ID|  
|RecordNumber|xs:long|내보낸 레코드의 시퀀스 번호|  
|EventTime|xs:dateTime|이벤트를 내보낸 시간(UTC)|  
|시스템 상태|xs:string|활동의 상태|  
|이름|xs:string|이벤트를 내보낸 활동의 표시 이름|  
|ActivityId|xs:string|내보내는 활동의 활동 ID|  
|ActivityInstanceId|xs:string|내보내는 활동의 활동 인스턴스 ID|  
|ActivityTypeName|xs:string|내보내는 활동의 형식 이름|  
|인수|xs:string|이 이벤트와 함께 추적된 인수입니다.  값은 xml 요소에 argumentValue 형식으로 저장 됩니다 \<items> \< item  name = "argumentName" type="System.String"> \</item> \</items> .  추적 된 인수가 없으면 문자열에가 포함 \<items/> 됩니다. ETW 이벤트 크기는 ETW 버퍼 크기 또는 ETW 이벤트의 최대 페이로드에 따라 제한됩니다. 이벤트 크기가 ETW 제한을 초과 하면 주석을 삭제 하 고 주석 값을 ...로 대체 하 여 이벤트를 자릅니다. \<items> \</items>  다음 형식은 ToString ()에서 반환 된 값으로 저장 됩니다. string, char, bool, int, short, long, uint, ushort, ulong, system.string, float, double, system.string, system.string, System.web.  모든 다른 형식은 System.Runtime.Serialization.NetDataContractSerializer를 사용하여 serialize됩니다.|  
|변수|xs:string|이 이벤트와 함께 추적된 변수입니다.  값은 xml 요소에 variableValue 형식으로 저장 됩니다 \<items> \< item  name = "variableName" type="System.String"> \</item> \</items> .  추적 된 변수가 없으면 문자열에가 포함 \<items/> 됩니다. ETW 이벤트 크기는 ETW 버퍼 크기 또는 ETW 이벤트의 최대 페이로드에 따라 제한됩니다. 이벤트 크기가 ETW 제한을 초과 하면 주석을 삭제 하 고 변수 값을 ...로 대체 하 여 이벤트를 자릅니다. \<items> \</items>  다음 형식은 ToString ()에서 반환 된 값으로 저장 됩니다. string, char, bool, int, short, long, uint, ushort, ulong, system.string, float, double, system.string, system.string, System.web.  모든 다른 형식은 System.Runtime.Serialization.NetDataContractSerializer를 사용하여 serialize됩니다.|  
|주석|xs:string|이 이벤트에 추가된 주석입니다.  값은 xml 요소에 a 형식으로 저장 됩니다 \<items> \< item  name = "annotationName" type="System.String"> \</item> \</items> .  주석을 지정 하지 않으면 문자열에가 포함 \<items/> 됩니다. ETW 이벤트 크기는 ETW 버퍼 크기 또는 ETW 이벤트의 최대 페이로드에 따라 제한됩니다. 이벤트 크기가 ETW 제한을 초과 하면 주석을 삭제 하 고 주석 값을 ...로 대체 하 여 이벤트를 자릅니다. \<items> \</items>|  
|ProfileName|xs:string|이 이벤트를 내보낸 이름 또는 추적 프로필|  
|HostReference|xs:string|웹 호스팅 서비스의 경우 이 필드는 웹 계층의 서비스를 고유하게 식별합니다.  해당 형식은 ' 웹 사이트 이름 응용 프로그램 가상 경로&#124;서비스 가상 경로&#124;ServiceName ' 예: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '로 정의 됩니다.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.|
