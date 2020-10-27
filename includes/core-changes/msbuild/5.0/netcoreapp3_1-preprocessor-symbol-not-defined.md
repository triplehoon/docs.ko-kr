---
ms.openlocfilehash: de35df21d1887bc95a3106edba312c53daad8b68
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654742"
---
### <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a><span data-ttu-id="63bab-101">.NET 5를 대상으로 하는 경우 NETCOREAPP3_1 전처리기 기호가 정의되지 않음</span><span class="sxs-lookup"><span data-stu-id="63bab-101">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>

<span data-ttu-id="63bab-102">.NET 5.0 RC2 이상 버전에서는 프로젝트에서 이전 버전의 전처리기 기호를 더 이상 정의하지 않고 대상으로 하는 버전의 기호만 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-102">In .NET 5.0 RC2 and later versions, projects no longer define preprocessor symbols for earlier versions, but only for the version that they target.</span></span> <span data-ttu-id="63bab-103">이는 .NET Core 1.0~3.1과 동일한 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-103">This is the same behavior as .NET Core 1.0 - 3.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="63bab-104">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="63bab-104">Version introduced</span></span>

<span data-ttu-id="63bab-105">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="63bab-105">5.0 RC2</span></span>

#### <a name="change-description"></a><span data-ttu-id="63bab-106">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="63bab-106">Change description</span></span>

<span data-ttu-id="63bab-107">.NET 5.0 미리 보기 7~RC1에서는 `net5.0`을 대상으로 하는 프로젝트에서 `NETCOREAPP3_1` 및 `NET5_0` 전처리기 기호를 모두 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-107">In .NET 5.0 preview 7 through RC1, projects that target `net5.0` define both `NETCOREAPP3_1` and `NET5_0` preprocessor symbols.</span></span> <span data-ttu-id="63bab-108">이와 같이 동작을 변경하는 이유는 .NET 5.0부터 조건부 컴파일 [기호가 누적되기](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols) 때문이었습니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-108">The intent behind this behavior change was that starting with .NET 5.0, conditional compilation [symbols would be cumulative](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span></span>

<span data-ttu-id="63bab-109">.NET 5.0 RC2 이상에서는 프로젝트에서 이전 버전이 아니라 대상으로 하는 TFM(대상 프레임워크 모니커)의 기호만 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-109">In .NET 5.0 RC2 and later, projects only define symbols for the target framework monikers (TFM) that it targets and not for any earlier versions.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="63bab-110">변경 이유</span><span class="sxs-lookup"><span data-stu-id="63bab-110">Reason for change</span></span>

<span data-ttu-id="63bab-111">고객 피드백을 반영하여 미리 보기 7의 변경 내용을 되돌렸습니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-111">The change from preview 7 was reverted due to customer feedback.</span></span> <span data-ttu-id="63bab-112">이전 버전의 기호를 정의하면 고객이 놀라거나 혼동했으며 일부 고객은 C# 컴파일러의 버그로 여기기도 했습니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-112">Defining symbols for earlier versions surprised and confused customers, and some assumed it was a bug in the C# compiler.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="63bab-113">권장 조치</span><span class="sxs-lookup"><span data-stu-id="63bab-113">Recommended action</span></span>

<span data-ttu-id="63bab-114">프로젝트가 `net5.0` 이상을 대상으로 하는 경우 `#if` 논리에서 `NETCOREAPP3_1`이 정의되어 있다고 간주하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-114">Make sure that your `#if` logic doesn't assume that `NETCOREAPP3_1` is defined when the project targets `net5.0` or higher.</span></span> <span data-ttu-id="63bab-115">대신, 프로젝트가 명시적으로 `netcoreapp3.1`을 대상으로 하는 경우에만 `NETCOREAPP3_1`이 정의되어 있다고 간주하세요.</span><span class="sxs-lookup"><span data-stu-id="63bab-115">Instead, assume that `NETCOREAPP3_1` is only defined when the project explicitly targets `netcoreapp3.1`.</span></span>

<span data-ttu-id="63bab-116">예를 들어 프로젝트가 .NET Core 2.1 및 .NET Core 3.1을 멀티 타기팅하고 .NET Core 3.1에 도입된 API를 호출하는 경우 `#if` 논리는 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="63bab-116">For example, if your project multitargets for .NET Core 2.1 and .NET Core 3.1 and you call APIs that were introduced in .NET Core 3.1, your `#if` logic should look as follows:</span></span>

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

#### <a name="category"></a><span data-ttu-id="63bab-117">범주</span><span class="sxs-lookup"><span data-stu-id="63bab-117">Category</span></span>

<span data-ttu-id="63bab-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="63bab-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="63bab-119">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="63bab-119">Affected APIs</span></span>

<span data-ttu-id="63bab-120">N/A</span><span class="sxs-lookup"><span data-stu-id="63bab-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->