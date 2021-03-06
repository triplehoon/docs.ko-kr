---
title: dotnet-counters 진단 도구 - .NET CLI
description: 임시 상태 모니터링 및 1단계 수준 성능을 위해 dotnet-counter CLI 도구를 설치하고 사용하는 방법을 알아봅니다.
ms.date: 11/17/2020
ms.openlocfilehash: 48e3b038ddb5c9421367612a592c5ba6b9459791
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009549"
---
# <a name="investigate-performance-counters-dotnet-counters"></a>성능 카운터 조사(dotnet-counters)

**이 문서의 적용 대상:**  ✔️ .NET Core 3.0 SDK 이상 버전

## <a name="install"></a>설치

다음 두 가지 방법으로 `dotnet-counters`를 다운로드하고 설치할 수 있습니다.

- **dotnet 전역 도구:**

  `dotnet-counters` [NuGet 패키지](https://www.nuget.org/packages/dotnet-counters)의 최신 릴리스 버전을 설치하려면 [dotnet tool install](../tools/dotnet-tool-install.md) 명령을 사용합니다.

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- **직접 다운로드:**

  플랫폼에 맞는 도구 실행 파일을 다운로드합니다.

  | OS  | 플랫폼 |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-counters/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64) |

## <a name="synopsis"></a>개요

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>설명

`dotnet-counters`는 임시 상태 모니터링 및 1단계 수준 성능 조사를 위한 성능 모니터링 도구입니다. <xref:System.Diagnostics.Tracing.EventCounter> API를 통해 게시된 성능 카운터 값을 관찰할 수 있습니다. 예를 들어, `PerfView` 또는 `dotnet-trace`를 사용하여 보다 심각한 성능 조사를 살펴보기 전에 의심스러운 내용이 있는지 확인하기 위해 .NET Core 애플리케이션에서 throw되는 CPU 사용량 또는 예외 비율과 같은 항목을 신속하게 모니터링할 수 있습니다.

## <a name="options"></a>옵션

- **`--version`**

  dotnet-counters 유틸리티의 버전을 표시합니다.

- **`-h|--help`**

  명령줄 도움말을 표시합니다.

## <a name="commands"></a>명령

| 명령                                             |
|-----------------------------------------------------|
| [dotnet-counters collect](#dotnet-counters-collect) |
| [dotnet-counters 목록](#dotnet-counters-list)       |
| [dotnet-counters 모니터](#dotnet-counters-monitor) |
| [dotnet-counters ps](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a>dotnet-counters collect

선택한 카운터 값을 주기적으로 수집하고 후처리를 위해 지정된 파일 형식으로 내보냅니다.

### <a name="synopsis"></a>개요

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a>옵션

- **`-p|--process-id <PID>`**

  카운터 데이터를 수집할 프로세스의 ID입니다.

- **`-n|--name <name>`**

  카운터 데이터를 수집할 프로세스의 이름입니다.

- **`--diagnostic-port`**

  만들 진단 포트의 이름입니다. 이 옵션을 사용하여 앱 시작부터 카운터 모니터링을 시작하는 방법은 [진단 포트 사용](#using-diagnostic-port)을 참조하세요.

- **`--refresh-interval <SECONDS>`**

  표시된 카운터 업데이트 사이의 지연 시간(초)입니다.

- **`--counters <COUNTERS>`**

  쉼표로 구분된 카운터 목록입니다. 카운터는 `provider_name[:counter_name]`을 지정할 수 있습니다. 적격 카운터 목록 없이 `provider_name`이 사용되는 경우 공급자의 모든 카운터가 표시됩니다. 공급자 및 카운터 이름을 검색하려면 [dotnet-counters 목록](#dotnet-counters-list) 명령을 사용합니다.

- **`--format <csv|json>`**

  내보낼 형식입니다. 현재 csv와 json을 사용할 수 있습니다.

- **`-o|--output <output>`**

  출력 파일의 이름입니다.

- **`-- <command>`(.NET 5.0 이상을 실행하는 대상 애플리케이션만 해당)**

  사용자는 컬렉션 구성 매개 변수 다음에 `--`와 명령을 차례로 추가하여 5.0 런타임 이상에서 .NET 애플리케이션을 시작할 수 있습니다. `dotnet-counters`는 제공된 명령을 사용하여 프로세스를 시작하고 요청된 메트릭을 수집합니다. 이 옵션은 애플리케이션의 시작 경로에 대한 메트릭을 수집하는 데 유용하며, 주요 진입점 이전이나 바로 다음에 발생하는 문제를 진단하거나 모니터링하는 데 사용할 수 있습니다.

  > [!NOTE]
  > 이 옵션을 사용하면 도구에 다시 전달되는 첫 번째 .NET 5.0 프로세스가 모니터링됩니다. 즉, 명령에서 여러 .NET 애플리케이션을 시작하는 경우 첫 번째 앱만 수집합니다. 따라서 자체 포함 애플리케이션에서 이 옵션을 사용하거나 `dotnet exec <app.dll>` 옵션을 사용하는 것이 좋습니다.

  > [!NOTE]
  > dotnet-counters를 통해 .NET 실행 파일을 시작하면 해당 입출력이 리디렉션되어 stdin/stdout과 상호 작용할 수 없습니다. Ctrl+C 또는 SIGTERM을 통해 도구를 종료하면 도구와 자식 프로세스가 모두 안전하게 종료됩니다. 자식 프로세스가 도구보다 먼저 종료되면 도구도 종료되고 추적을 안전하게 볼 수 있습니다. Stdin/stdout을 사용해야 하는 경우 `--diagnostic-port` 옵션을 사용할 수 있습니다. 자세한 내용은 [진단 포트 사용](#using-diagnostic-port)을 참조하세요.

### <a name="examples"></a>예

- 3초의 새로 고침 간격으로 모든 카운터를 수집하고 csv를 출력으로 생성합니다.

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- `dotnet mvc.dll`을 자식 프로세스로 시작하고 시작에서 런타임 카운터 및 ASP.NET Core 호스팅 카운터 수집을 시작하여 JSON 출력으로 저장합니다.

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a>dotnet-counters 목록

공급자별로 그룹화된 카운터 이름 및 설명 목록을 표시합니다.

### <a name="synopsis"></a>개요

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>예제

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> 이러한 카운터를 지원하는 프로세스를 식별한 경우, 예를 들어 호스트 머신에서 ASP.NET Core 애플리케이션이 실행되고 있는 경우 `Microsoft.AspNetCore.Hosting` 카운터가 표시됩니다.

## <a name="dotnet-counters-monitor"></a>dotnet-counters 모니터

선택한 카운터의 값을 주기적으로 새로 고치는 방법을 표시합니다.

### <a name="synopsis"></a>개요

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a>옵션

- **`-p|--process-id <PID>`**

  모니터링할 프로세스의 ID입니다.

- **`-n|--name <name>`**

  모니터링할 프로세스의 이름입니다.

- **`--diagnostic-port`**

  만들 진단 포트의 이름입니다. 이 옵션을 사용하여 앱 시작부터 카운터 모니터링을 시작하는 방법은 [진단 포트 사용](#using-diagnostic-port)을 참조하세요.

- **`--refresh-interval <SECONDS>`**

  표시된 카운터 업데이트 사이의 지연 시간(초)입니다.

- **`--counters <COUNTERS>`**

  쉼표로 구분된 카운터 목록입니다. 카운터는 `provider_name[:counter_name]`을 지정할 수 있습니다. 적격 카운터 목록 없이 `provider_name`이 사용되는 경우 공급자의 모든 카운터가 표시됩니다. 공급자 및 카운터 이름을 검색하려면 [dotnet-counters 목록](#dotnet-counters-list) 명령을 사용합니다.

 **`-- <command>`(.NET 5.0 이상을 실행하는 대상 애플리케이션만 해당)**

  사용자는 컬렉션 구성 매개 변수 다음에 `--`와 명령을 차례로 추가하여 5.0 런타임 이상에서 .NET 애플리케이션을 시작할 수 있습니다. `dotnet-counters`는 제공된 명령을 사용하여 프로세스를 시작하고 요청된 메트릭을 모니터링합니다. 이 옵션은 애플리케이션의 시작 경로에 대한 메트릭을 수집하는 데 유용하며, 주요 진입점 이전이나 바로 다음에 발생하는 문제를 진단하거나 모니터링하는 데 사용할 수 있습니다.

  > [!NOTE]
  > 이 옵션을 사용하면 도구에 다시 전달되는 첫 번째 .NET 5.0 프로세스가 모니터링됩니다. 즉, 명령에서 여러 .NET 애플리케이션을 시작하는 경우 첫 번째 앱만 수집합니다. 따라서 자체 포함 애플리케이션에서 이 옵션을 사용하거나 `dotnet exec <app.dll>` 옵션을 사용하는 것이 좋습니다.

  > [!NOTE]
  > dotnet-counters를 통해 .NET 실행 파일을 시작하면 해당 입출력이 리디렉션되어 stdin/stdout과 상호 작용할 수 없습니다. Ctrl+C 또는 SIGTERM을 통해 도구를 종료하면 도구와 자식 프로세스가 모두 안전하게 종료됩니다. 자식 프로세스가 도구보다 먼저 종료되면 도구도 종료되고 추적을 안전하게 볼 수 있습니다. Stdin/stdout을 사용해야 하는 경우 `--diagnostic-port` 옵션을 사용할 수 있습니다. 자세한 내용은 [진단 포트 사용](#using-diagnostic-port)을 참조하세요.

### <a name="examples"></a>예

- 3초의 새로 고침 간격으로 `System.Runtime`의 모든 카운터를 모니터링합니다.

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- `System.Runtime`에서 CPU 사용량 및 GC 힙 크기만 모니터링합니다.

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- 사용자 정의 `EventSource`에서 `EventCounter` 값을 모니터링합니다. 자세한 내용은 [자습서: .NET Core에서 EventCounters를 사용하여 성능 측정](event-counter-perf.md)을 참조하세요.

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- `my-aspnet-server.exe`를 시작하고 시작에서 로드된 어셈블리 수를 모니터링합니다(.NET 5.0 이상만 해당).

  > [!IMPORTANT]
  > .NET 5.0 이상을 실행하는 앱에만 적용됩니다.

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- `arg1` 및 `arg2`를 명령줄 인수로 사용하여 `my-aspnet-server.exe`를 시작하고 시작에서 작업 집합 및 GC 힙 크기를 모니터링합니다(.NET 5.0 이상만 해당).

  > [!IMPORTANT]
  > .NET 5.0 이상을 실행하는 앱에만 적용됩니다.

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a>dotnet-counters ps

모니터링할 수 있는 dotnet 프로세스의 목록을 표시합니다.

### <a name="synopsis"></a>개요

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>예제

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a>진단 포트 사용

  > [!IMPORTANT]
  > .NET 5.0 이상을 실행하는 앱에만 적용됩니다.

진단 포트는 .NET 5에서 추가된 새로운 런타임 기능으로, 앱 시작부터 카운터 모니터링과 수집을 시작하는 데 사용할 수 있습니다. `dotnet-counters`를 사용하여 이렇게 하려면 위의 예제에 설명된 대로 `dotnet-counters <collect|monitor> -- <command>`를 사용하거나 `--diagnostic-port` 옵션을 사용할 수 있습니다.

`dotnet-counters <collect|monitor> -- <command>`를 사용하여 애플리케이션을 자식 프로세스로 실행하는 것이 시작부터 빠르게 모니터링하는 가장 간단한 방법입니다.

하지만 모니터링되는 앱의 수명을 더 세부적으로 제어하거나(예: 처음 10분간만 앱을 모니터링하고 실행 계속) CLI를 사용하여 앱을 조작해야 하는 경우에는 `--diagnostic-port` 옵션을 사용하여 모니터링되는 대상 앱과 `dotnet-counters`를 모두 제어할 수 있습니다.

1. 아래 명령은 dotnet-counters에서 `myport.sock`라는 진단 소켓을 만들고 연결을 대기하게 합니다.

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    출력:

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. 별도의 콘솔에서 `DOTNET_DiagnosticPorts` 환경 변수를 `dotnet-counters` 출력의 값으로 설정하고 대상 애플리케이션을 시작합니다.

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    그러면 `dotnet-counters`가 `my-dotnet-app`에서 카운터 수집을 시작할 수 있습니다.

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > `dotnet run`을 사용하여 앱을 시작하면 문제가 될 수 있는데, dotnet CLI가 앱이 아닌 여러 자식 프로세스를 생성할 수 있고 해당 프로세스가 앱보다 먼저 `dotnet-counters`에 연결하여 앱이 런타임에 일시 중단될 수 있기 때문입니다. 앱의 자체 포함 버전을 직접 사용하거나 `dotnet exec`를 사용하여 애플리케이션을 시작하는 것이 좋습니다.
