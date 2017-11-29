---
title: "トレースの種類の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8e82f153e996ffebc2aba614f42c5cfa949e7ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="trace-type-summary"></a><span data-ttu-id="9f89a-102">トレースの種類の概要</span><span class="sxs-lookup"><span data-stu-id="9f89a-102">Trace Type Summary</span></span>
<span data-ttu-id="9f89a-103">[Sourcelevels](http://go.microsoft.com/fwlink/?LinkID=94943)さまざまなトレース レベルを定義します。 重大なエラー、警告、情報、および Verbose も同様の説明、`ActivityTracing`の出力を切り替えるかをフラグは、境界とアクティビティ転送イベントをトレースします。</span><span class="sxs-lookup"><span data-stu-id="9f89a-103">[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="9f89a-104">確認することも[TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169)から出力できるトレースの種類の<xref:System.Diagnostics>します。</span><span class="sxs-lookup"><span data-stu-id="9f89a-104">You can also review [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="9f89a-105">最も重要な種類を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9f89a-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="9f89a-106">トレースの種類</span><span class="sxs-lookup"><span data-stu-id="9f89a-106">Trace Type</span></span>|<span data-ttu-id="9f89a-107">説明</span><span class="sxs-lookup"><span data-stu-id="9f89a-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="9f89a-108">Critical</span><span class="sxs-lookup"><span data-stu-id="9f89a-108">Critical</span></span>|<span data-ttu-id="9f89a-109">致命的なエラーまたはアプリケーションのクラッシュ。</span><span class="sxs-lookup"><span data-stu-id="9f89a-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="9f89a-110">Error</span><span class="sxs-lookup"><span data-stu-id="9f89a-110">Error</span></span>|<span data-ttu-id="9f89a-111">回復可能なエラー。</span><span class="sxs-lookup"><span data-stu-id="9f89a-111">Recoverable error.</span></span>|  
|<span data-ttu-id="9f89a-112">警告</span><span class="sxs-lookup"><span data-stu-id="9f89a-112">Warning</span></span>|<span data-ttu-id="9f89a-113">情報メッセージ。</span><span class="sxs-lookup"><span data-stu-id="9f89a-113">Informational message.</span></span>|  
|<span data-ttu-id="9f89a-114">情報</span><span class="sxs-lookup"><span data-stu-id="9f89a-114">Information</span></span>|<span data-ttu-id="9f89a-115">重大ではない問題。</span><span class="sxs-lookup"><span data-stu-id="9f89a-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="9f89a-116">詳細</span><span class="sxs-lookup"><span data-stu-id="9f89a-116">Verbose</span></span>|<span data-ttu-id="9f89a-117">トレースのデバッグ。</span><span class="sxs-lookup"><span data-stu-id="9f89a-117">Debugging trace.</span></span>|  
|<span data-ttu-id="9f89a-118">開始</span><span class="sxs-lookup"><span data-stu-id="9f89a-118">Start</span></span>|<span data-ttu-id="9f89a-119">処理の論理単位の開始。</span><span class="sxs-lookup"><span data-stu-id="9f89a-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9f89a-120">Suspend</span><span class="sxs-lookup"><span data-stu-id="9f89a-120">Suspend</span></span>|<span data-ttu-id="9f89a-121">処理の論理単位の中断。</span><span class="sxs-lookup"><span data-stu-id="9f89a-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9f89a-122">Resume</span><span class="sxs-lookup"><span data-stu-id="9f89a-122">Resume</span></span>|<span data-ttu-id="9f89a-123">処理の論理単位の再開。</span><span class="sxs-lookup"><span data-stu-id="9f89a-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9f89a-124">停止</span><span class="sxs-lookup"><span data-stu-id="9f89a-124">Stop</span></span>|<span data-ttu-id="9f89a-125">処理の論理単位の停止。</span><span class="sxs-lookup"><span data-stu-id="9f89a-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9f89a-126">転送</span><span class="sxs-lookup"><span data-stu-id="9f89a-126">Transfer</span></span>|<span data-ttu-id="9f89a-127">相関 ID の変更。</span><span class="sxs-lookup"><span data-stu-id="9f89a-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="9f89a-128">アクティビティは、上記のトレースの種類の組み合わせとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="9f89a-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="9f89a-129">ローカル (トレース ソース) スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9f89a-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="9f89a-130">これは、アクティビティが次の条件を満たす必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9f89a-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="9f89a-131">アクティビティは、Start トレースによって開始し、Stop トレースによって停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f89a-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="9f89a-132">Suspend トレースまたは Resume トレースの直前に Transfer トレースが必要です。</span><span class="sxs-lookup"><span data-stu-id="9f89a-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="9f89a-133">Suspend トレースと Resume トレースが存在する場合、これらのトレースの間にトレースが存在することはできません。</span><span class="sxs-lookup"><span data-stu-id="9f89a-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="9f89a-134">上記の条件を満たしている限り、Critical/Error/Warning/Information/Verbose/Transfer の各トレースはいくつでも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9f89a-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="9f89a-135">グローバル スコープでの典型的なアクティビティを定義する正規表現は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9f89a-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="9f89a-136">R はローカル スコープのアクティビティを表す正規表現です。</span><span class="sxs-lookup"><span data-stu-id="9f89a-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="9f89a-137">これは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9f89a-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
