---
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 9f97e74e7685d57b487f456625826ee9cd8e1760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457349"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="275b3-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="275b3-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="275b3-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="275b3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="275b3-104">ID</span><span class="sxs-lookup"><span data-stu-id="275b3-104">ID</span></span>|<span data-ttu-id="275b3-105">207</span><span class="sxs-lookup"><span data-stu-id="275b3-105">207</span></span>|  
|<span data-ttu-id="275b3-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="275b3-106">Keywords</span></span>|<span data-ttu-id="275b3-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="275b3-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="275b3-108">レベル</span><span class="sxs-lookup"><span data-stu-id="275b3-108">Level</span></span>|<span data-ttu-id="275b3-109">情報</span><span class="sxs-lookup"><span data-stu-id="275b3-109">Information</span></span>|  
|<span data-ttu-id="275b3-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="275b3-110">Channel</span></span>|<span data-ttu-id="275b3-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="275b3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="275b3-112">説明</span><span class="sxs-lookup"><span data-stu-id="275b3-112">Description</span></span>  
 <span data-ttu-id="275b3-113">このイベントは、`FaultProvider` が呼び出された後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="275b3-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="275b3-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="275b3-114">Message</span></span>  
 <span data-ttu-id="275b3-115">ディスパッチャーが型 '%1' の FaultProvider を呼び出し、種類 '%2' の例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="275b3-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="275b3-116">詳細</span><span class="sxs-lookup"><span data-stu-id="275b3-116">Details</span></span>  
  
|<span data-ttu-id="275b3-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="275b3-117">Data Item Name</span></span>|<span data-ttu-id="275b3-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="275b3-118">Data Item Type</span></span>|<span data-ttu-id="275b3-119">説明</span><span class="sxs-lookup"><span data-stu-id="275b3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="275b3-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="275b3-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="275b3-121">呼び出された `FaultProvider` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="275b3-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="275b3-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="275b3-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="275b3-123">`FaultProvider` の操作対象である例外の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="275b3-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="275b3-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="275b3-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="275b3-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="275b3-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="275b3-126">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="275b3-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="275b3-127">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="275b3-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="275b3-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="275b3-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="275b3-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="275b3-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
