---
title: ICorProfilerInfo 인터페이스
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
ms.openlocfilehash: a029784a28036e531670ad373893b4256c5864c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671189"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo 인터페이스

코드 프로파일러가 CLR (공용 언어 런타임)과 통신 하 여 이벤트 모니터링과 요청 정보를 제어 하는 데 사용할 수 있는 메서드를 제공 합니다.  
  
> [!NOTE]
> 인터페이스의 각 메서드 `ICorProfilerInfo` 는 성공 또는 실패를 나타내는 HRESULT를 반환 합니다. 가능한 반환 코드 목록은 CorError .h를 참조 하세요.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[BeginInprocDebugging 메서드](icorprofilerinfo-begininprocdebugging-method.md)|In-process 디버깅 지원 기능을 초기화 합니다. 이 메서드는 .NET Framework 버전 2.0에서 사용 되지 않습니다.|  
|[EndInprocDebugging 메서드](icorprofilerinfo-endinprocdebugging-method.md)|In-process 디버깅 세션을 종료 합니다. 이 메서드는 .NET Framework 버전 2.0에서 사용 되지 않습니다.|  
|[ForceGC 메서드](icorprofilerinfo-forcegc-method.md)|런타임 내에서 가비지 수집을 강제로 수행 합니다.|  
|[GetAppDomainInfo 메서드](icorprofilerinfo-getappdomaininfo-method.md)|지정 된 응용 프로그램 도메인에 대 한 정보를 가져옵니다.|  
|[GetAssemblyInfo 메서드](icorprofilerinfo-getassemblyinfo-method.md)|지정 된 어셈블리에 대 한 정보를 가져옵니다.|  
|[GetClassFromObject 메서드](icorprofilerinfo-getclassfromobject-method.md)|의를 가져옵니다. `ClassID`<br /><br /> 지정 된 개체 `ObjectID` 입니다.|  
|[GetClassFromToken 메서드](icorprofilerinfo-getclassfromtoken-method.md)|메타 데이터 토큰이 지정 된 경우 클래스의 ID를 가져옵니다. 이 메서드는 .NET Framework 버전 2.0에서 사용 되지 않습니다. 대신 [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) 메서드를 사용 합니다.|  
|[GetClassIDInfo 메서드](icorprofilerinfo-getclassidinfo-method.md)|지정 된 클래스에 대 한 부모 모듈과 메타 데이터 토큰을 가져옵니다.|  
|[GetCodeInfo 메서드](icorprofilerinfo-getcodeinfo-method.md)|지정된 함수 ID와 연결된 네이티브 코드의 범위를 가져옵니다. 이 메서드는 사용되지 않습니다. 대신 [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) 메서드를 사용 합니다.|  
|[GetCurrentThreadID 메서드](icorprofilerinfo-getcurrentthreadid-method.md)|관리 되는 스레드인 경우 현재 스레드의 ID를 가져옵니다.|  
|[GetEventMask 메서드](icorprofilerinfo-geteventmask-method.md)|프로파일러가 CLR에서 이벤트 알림을 받으려는 현재 이벤트 범주를 가져옵니다.|  
|[GetFunctionFromIP 메서드](icorprofilerinfo-getfunctionfromip-method.md)|관리 되는 코드 명령 포인터를에 매핑합니다 `FunctionID` .|  
|[GetFunctionFromToken 메서드](icorprofilerinfo-getfunctionfromtoken-method.md)|함수의 ID를 가져옵니다. 이 메서드는 .NET Framework 버전 2.0에서 사용 되지 않습니다. 대신 [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) 메서드를 사용 합니다.|  
|[GetFunctionInfo 메서드](icorprofilerinfo-getfunctioninfo-method.md)|지정 된 함수에 대 한 부모 클래스 및 메타 데이터 토큰을 가져옵니다.|  
|[GetHandleFromThread 메서드](icorprofilerinfo-gethandlefromthread-method.md)|스레드의 ID를 Win32 스레드 핸들에 매핑합니다.|  
|[GetILFunctionBody 메서드](icorprofilerinfo-getilfunctionbody-method.md)|MSIL (Microsoft 중간 언어) 코드에서 헤더를 시작 하는 메서드의 본문에 대 한 포인터를 가져옵니다.|  
|[GetILFunctionBodyAllocator 메서드](icorprofilerinfo-getilfunctionbodyallocator-method.md)|MSIL 코드에서 메서드의 본문을 바꾸는 데 사용 되는 메모리를 할당 하는 메서드를 제공 하는 인터페이스를 가져옵니다.|  
|[GetILToNativeMapping 메서드](icorprofilerinfo-getiltonativemapping-method.md)|MSIL 오프셋에서 지정 된 함수에 포함 된 코드에 대 한 네이티브 오프셋으로의 맵을 가져옵니다.|  
|[GetInprocInspectionInterface 메서드](icorprofilerinfo-getinprocinspectioninterface-method.md)|ICorDebugProcess 인터페이스에 대해 쿼리할 수 있는 개체를 가져옵니다. 이 메서드는 .NET Framework 버전 2.0에서 사용 되지 않습니다.|  
|[GetInprocInspectionIThisThread 메서드](icorprofilerinfo-getinprocinspectionithisthread-method.md)|ICorDebugThread 인터페이스에 대해 쿼리할 수 있는 개체를 가져옵니다. 이 메서드는 .NET Framework 버전 2.0에서 사용 되지 않습니다.|  
|[GetModuleInfo 메서드](icorprofilerinfo-getmoduleinfo-method.md)|모듈 ID가 지정된 경우 모듈의 파일 이름 및 모듈의 부모 어셈블리 ID를 반환합니다.|  
|[GetModuleMetaData 메서드](icorprofilerinfo-getmodulemetadata-method.md)|지정 된 모듈에 매핑되는 메타 데이터 인터페이스 인스턴스를 가져옵니다.|  
|[GetObjectSize 메서드](icorprofilerinfo-getobjectsize-method.md)|지정 된 개체의 크기를 가져옵니다.|  
|[GetThreadContext 메서드](icorprofilerinfo-getthreadcontext-method.md)|지정 된 스레드와 현재 연결 된 컨텍스트 id를 가져옵니다.|  
|[GetThreadInfo 메서드](icorprofilerinfo-getthreadinfo-method.md)|지정 된 스레드에 대 한 현재 Win32 스레드 id를 가져옵니다.|  
|[GetTokenAndMetadataFromFunction 메서드](icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|지정 된 함수에 대 한 토큰에 대해 사용할 수 있는 메타 데이터 인터페이스 인스턴스와 메타 데이터 토큰을 가져옵니다.|  
|[IsArrayClass 메서드](icorprofilerinfo-isarrayclass-method.md)|지정 된 클래스가 배열 클래스 인지 여부를 확인 합니다.|  
|[SetEnterLeaveFunctionHooks 메서드](icorprofilerinfo-setenterleavefunctionhooks-method.md)|관리 되는 함수의 "enter", "leave" 및 "tailcall" 후크에 대해 호출 될 프로파일러 구현 함수를 지정 합니다.|  
|[SetEventMask 메서드](icorprofilerinfo-seteventmask-method.md)|프로파일러가 CLR에서 알림을 받으려는 이벤트 형식을 지정 하는 값을 설정 합니다.|  
|[SetFunctionIDMapper 메서드](icorprofilerinfo-setfunctionidmapper-method.md)|`FunctionID` 값을 대체 값에 매핑하기 위해 호출되는 프로파일러 구현 함수를 지정합니다. 대체 값은 프로파일러의 함수 진입점/종료점 후크에 전달됩니다.|  
|[SetFunctionReJIT 메서드](icorprofilerinfo-setfunctionrejit-method.md)|구현되지 않았습니다. 사용하지 마십시오.|  
|[SetILFunctionBody 메서드](icorprofilerinfo-setilfunctionbody-method.md)|지정 된 모듈에 있는 지정 된 함수의 본문을 바꿉니다.|  
|[SetILInstrumentedCodeMap 메서드](icorprofilerinfo-setilinstrumentedcodemap-method.md)|지정 된 함수의 원래 MSIL 오프셋이 함수의 프로파일러 수정 MSIL의 새 오프셋에 매핑되는 방법을 지정 합니다.|  
  
## <a name="remarks"></a>설명  

 프로파일러에서는 인터페이스의 메서드를 호출 `ICorProfilerInfo` 하 여 CLR과 통신 하 여 이벤트 모니터링과 요청 정보를 제어 합니다.  
  
 인터페이스의 메서드는 `ICorProfilerInfo` 자유 스레드된 모델을 사용 하 여 CLR에 의해 구현 됩니다. 각 메서드가 HRESULT를 반환하여 성공 또는 실패를 나타냅니다. 가능한 반환 코드 목록은 CorError .h를 참조 하세요.  
  
 CLR은 [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)의 프로파일러 구현을 통해 `ICorProfilerInfo` 초기화 하는 동안 각 코드 프로파일러에 대 한 인터페이스를 전달 합니다. 그런 다음 코드 프로파일러는 인터페이스의 메서드를 호출 `ICorProfilerInfo` 하 여 CLR의 컨트롤에서 실행 되는 관리 코드에 대 한 정보를 가져올 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [프로파일링 인터페이스](profiling-interfaces.md)
- [ICorProfilerInfo2 인터페이스](icorprofilerinfo2-interface.md)
