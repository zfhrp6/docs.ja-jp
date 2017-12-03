---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 670650c612ac01ab9c82028388a4524d2f08fd79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="16594-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="16594-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="16594-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="16594-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16594-104">ID</span><span class="sxs-lookup"><span data-stu-id="16594-104">ID</span></span>|<span data-ttu-id="16594-105">208</span><span class="sxs-lookup"><span data-stu-id="16594-105">208</span></span>|  
|<span data-ttu-id="16594-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="16594-106">Keywords</span></span>|<span data-ttu-id="16594-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="16594-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="16594-108">レベル</span><span class="sxs-lookup"><span data-stu-id="16594-108">Level</span></span>|<span data-ttu-id="16594-109">情報</span><span class="sxs-lookup"><span data-stu-id="16594-109">Information</span></span>|  
|<span data-ttu-id="16594-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="16594-110">Channel</span></span>|<span data-ttu-id="16594-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="16594-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16594-112">説明</span><span class="sxs-lookup"><span data-stu-id="16594-112">Description</span></span>  
 <span data-ttu-id="16594-113">このイベントは、メッセージ インスペクターで Service Model が `AfterReceive` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="16594-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="16594-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="16594-114">Message</span></span>  
 <span data-ttu-id="16594-115">ディスパッチャーが型 '%1' の MessageInspector で 'AfterReceiveReply' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="16594-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16594-116">詳細</span><span class="sxs-lookup"><span data-stu-id="16594-116">Details</span></span>  
  
|<span data-ttu-id="16594-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="16594-117">Data Item Name</span></span>|<span data-ttu-id="16594-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="16594-118">Data Item Type</span></span>|<span data-ttu-id="16594-119">説明</span><span class="sxs-lookup"><span data-stu-id="16594-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16594-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="16594-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="16594-121">呼び出された `MessageInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="16594-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="16594-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="16594-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="16594-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="16594-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="16594-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="16594-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="16594-125">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="16594-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="16594-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="16594-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="16594-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="16594-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
