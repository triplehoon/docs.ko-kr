---
title: HTTP, TCP 또는 명명된 파이프를 사용하는 비동기 시나리오
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 00213c8d117f4319d7e29312dd0b9805d916231a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244147"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP 또는 명명된 파이프를 사용하는 비동기 시나리오

이 항목에서는 HTTP, TCP 또는 명명된 파이프를 사용하는 다중 스레드 요청이 포함된 다양한 비동기 request/reply 시나리오의 작업 및 전송에 대해 설명합니다.  
  
## <a name="asynchronous-requestreply-without-errors"></a>오류가 없는 비동기 Request/Reply  

 이 단원에서는 다중 스레드 클라이언트에서의 비동기 request/reply 시나리오 작업 및 전송에 대해 설명합니다.  
  
 `beginCall`이 반환되고 `endCall`이 반환되면 호출자 작업이 종료됩니다. 콜백을 호출하면 콜백이 반환됩니다.  
  
 `beginCall`이 반환되거나, `endCall`이 반환되거나, 작업에서 호출한 경우 콜백이 반환되면 호출된 작업이 종료됩니다.  
  
### <a name="asynchronous-client-without-callback"></a>콜백이 없는 비동기 클라이언트  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>전파는 양쪽 모두에서 HTTP를 사용하여 활성화됩니다.  

 ![PropagateActivity가 true로 설정 된 경우 콜백이 없는 비동기 클라이언트입니다.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 인 경우 `propagateActivity=true` processmessage는 전송할 Processmessage 동작을 나타냅니다.  
  
 HTTP기반 시나리오의 경우 ReceiveBytes는 처음 보내는 메시지에서 호출되어 요청 수명이 끝날 때까지 존재합니다.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>HTTP를 사용하며 한쪽에서 전파가 비활성화  

 한쪽 `propagateActivity=false` 에 있는 경우 ProcessMessage는 전송할 Processmessage 동작을 나타내지 않습니다. 따라서 새 임시 ProcessAction 동작이 새 ID로 호출됩니다. 비동기 응답이 ServiceModel 모드에 있는 요청과 일치하는 경우 로컬 컨텍스트에서 작업 ID를 검색할 수 있습니다. 실제 ProcessAction 동작을 해당 ID와 함께 전송할 수 있습니다.  
  
 ![양쪽에서 propagateActivity가 false로 설정 된 콜백이 없는 비동기 클라이언트입니다.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 HTTP기반 시나리오의 경우 ReceiveBytes는 처음 보내는 메시지에서 호출되어 요청 수명이 끝날 때까지 존재합니다.  
  
 프로세스 동작 작업은 호출자 또는 호출 수신자에서 비동기 클라이언트에 생성 되 `propagateActivity=false` 고 응답 메시지에 작업 헤더가 포함 되지 않은 경우에 생성 됩니다.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>전파는 양쪽 모두에서 TCP 또는 명명된 파이프를 사용하여 활성화됩니다.  

 ![양쪽에서 propagateActivity가 true로 설정 되 고, 명명 된 파이프/TCP에서 콜백이 없는 비동기 클라이언트입니다.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 명명된 파이프 또는 TCP 기반 시나리오에서 ReceiveBytes는 클라이언트가 열리면 호출되어 연결이 지속되는 동안 존재합니다.  
  
 첫 번째 이미지와 마찬가지로 `propagateActivity=true` processmessage는 전송할 Processmessage 작업을 나타냅니다.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>전파는 한쪽에서 TCP 또는 명명된 파이프를 사용하여 비활성화됩니다.  

 명명된 파이프 또는 TCP 기반 시나리오에서 ReceiveBytes는 클라이언트가 열리면 호출되어 연결이 지속되는 동안 존재합니다.  
  
 두 번째 이미지와 마찬가지로 두 `propagateActivity=false` 쪽 모두에서 ProcessMessage는 전송할 Processmessage 작업을 나타내지 않습니다. 따라서 새 임시 ProcessAction 동작이 새 ID로 호출됩니다. 비동기 응답이 ServiceModel 모드에 있는 요청과 일치하는 경우 로컬 컨텍스트에서 작업 ID를 검색할 수 있습니다. 실제 ProcessAction 동작을 해당 ID와 함께 전송할 수 있습니다.  
  
 ![콜백이 없는 비동기 클라이언트는 양쪽 및 명명 된 파이프/TCP에서 propagateActivity가 false로 설정 됩니다.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a>콜백이 있는 비동기 클라이언트  

 이 시나리오에서는 콜백과 `endCall`에 G 및 A’ 작업과 출력/입력되는 전송을 추가합니다.  
  
 이 섹션에서는와 함께 HTTP를 사용 하는 방법을 보여 줍니다 `propagateActivity` = `true` . 그러나 추가 작업 및 전송은 다른 경우 (즉, `propagateActivity` = `false` TCP 또는 명명 된 파이프 사용)에도 적용 됩니다.  
  
 클라이언트에서 사용자 코드를 호출하여 결과가 준비된 것을 알리면 콜백에서 새 작업(G)을 만듭니다. 그러면 사용자 코드에서 콜백 내부(그림 5) 또는 콜백 외부(그림 6)로부터 `endCall`을 호출합니다. 에서 호출 되는 사용자 작업을 알 수 없기 때문에 `endCall` 이 활동에는 레이블이 지정 됩니다 `A’` . A’는 A와 같을 수도 있고 다를 수도 있습니다.  
  
 ![콜백이 콜백 인 비동기 클라이언트를 표시 합니다.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![콜백이 있는 비동기 클라이언트를 표시 합니다. 콜백이 외부에서 endcall입니다.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a>콜백이 있는 비동기 서버  

 ![콜백이 있는 비동기 서버를 표시 합니다.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 채널 스택에서는 메시지를 받으면 클라이언트를 콜백합니다. 이 처리의 추적은 ProcessRequest 작업 자체에서 내보냅니다.  
  
## <a name="asynchronous-requestreply-with-errors"></a>오류가 있는 Request/Reply  

 `endCall`을 수행하는 동안 오류 메시지 오류가 발생했습니다. 그 점을 제외한 작업과 전송은 이전 시나리오와 비슷합니다.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>오류가 있거나 없는 비동기 단방향  

 클라이언트에 응답이나 오류가 반환되지 않습니다.
