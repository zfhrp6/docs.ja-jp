---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 907f4404e234ada2cf084f531a4de8fcfc84d6c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="713e2-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="713e2-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="713e2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="713e2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="713e2-104">ID</span><span class="sxs-lookup"><span data-stu-id="713e2-104">ID</span></span>|<span data-ttu-id="713e2-105">201</span><span class="sxs-lookup"><span data-stu-id="713e2-105">201</span></span>|  
|<span data-ttu-id="713e2-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="713e2-106">Keywords</span></span>|<span data-ttu-id="713e2-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="713e2-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="713e2-108">レベル</span><span class="sxs-lookup"><span data-stu-id="713e2-108">Level</span></span>|<span data-ttu-id="713e2-109">情報</span><span class="sxs-lookup"><span data-stu-id="713e2-109">Information</span></span>|  
|<span data-ttu-id="713e2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="713e2-110">Channel</span></span>|<span data-ttu-id="713e2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="713e2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="713e2-112">説明</span><span class="sxs-lookup"><span data-stu-id="713e2-112">Description</span></span>  
 <span data-ttu-id="713e2-113">このイベントは、クライアント メッセージ インスペクターで Service Model が `AfterReceiveReply` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="713e2-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="713e2-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="713e2-114">Message</span></span>  
 <span data-ttu-id="713e2-115">ディスパッチャーが型 '%1' の ClientMessageInspector で 'AfterReceiveReply' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="713e2-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="713e2-116">詳細</span><span class="sxs-lookup"><span data-stu-id="713e2-116">Details</span></span>  
  
|<span data-ttu-id="713e2-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="713e2-117">Data Item Name</span></span>|<span data-ttu-id="713e2-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="713e2-118">Data Item Type</span></span>|<span data-ttu-id="713e2-119">説明</span><span class="sxs-lookup"><span data-stu-id="713e2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="713e2-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="713e2-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="713e2-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="713e2-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="713e2-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="713e2-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="713e2-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="713e2-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="713e2-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="713e2-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="713e2-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="713e2-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="713e2-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="713e2-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="713e2-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="713e2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
