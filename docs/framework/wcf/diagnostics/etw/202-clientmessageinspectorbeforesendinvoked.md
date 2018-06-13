---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 98de1d7e8e5e87ec7fbd783092f7fbc212fec65d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459356"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="e83ca-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="e83ca-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="e83ca-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e83ca-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e83ca-104">ID</span><span class="sxs-lookup"><span data-stu-id="e83ca-104">ID</span></span>|<span data-ttu-id="e83ca-105">202</span><span class="sxs-lookup"><span data-stu-id="e83ca-105">202</span></span>|  
|<span data-ttu-id="e83ca-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e83ca-106">Keywords</span></span>|<span data-ttu-id="e83ca-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e83ca-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e83ca-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e83ca-108">Level</span></span>|<span data-ttu-id="e83ca-109">情報</span><span class="sxs-lookup"><span data-stu-id="e83ca-109">Information</span></span>|  
|<span data-ttu-id="e83ca-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e83ca-110">Channel</span></span>|<span data-ttu-id="e83ca-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e83ca-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e83ca-112">説明</span><span class="sxs-lookup"><span data-stu-id="e83ca-112">Description</span></span>  
 <span data-ttu-id="e83ca-113">このイベントは、クライアント メッセージ インスペクターで Service Model が `BeforeSendRequest` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e83ca-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e83ca-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e83ca-114">Message</span></span>  
 <span data-ttu-id="e83ca-115">ディスパッチャーが型 '%1' の ClientMessageInspector で 'BeforeSendRequest' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="e83ca-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e83ca-116">説明</span><span class="sxs-lookup"><span data-stu-id="e83ca-116">Details</span></span>  
  
|<span data-ttu-id="e83ca-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e83ca-117">Data Item Name</span></span>|<span data-ttu-id="e83ca-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e83ca-118">Data Item Type</span></span>|<span data-ttu-id="e83ca-119">説明</span><span class="sxs-lookup"><span data-stu-id="e83ca-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e83ca-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="e83ca-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="e83ca-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="e83ca-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="e83ca-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="e83ca-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="e83ca-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="e83ca-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e83ca-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="e83ca-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e83ca-125">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="e83ca-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e83ca-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e83ca-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e83ca-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e83ca-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
