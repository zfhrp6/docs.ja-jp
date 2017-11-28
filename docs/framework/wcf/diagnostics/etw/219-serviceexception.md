---
title: 219 - ServiceException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dd38ab45bceeee577d9e33f699a03a81c09dfc99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="219---serviceexception"></a><span data-ttu-id="1b904-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="1b904-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="1b904-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1b904-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b904-104">ID</span><span class="sxs-lookup"><span data-stu-id="1b904-104">ID</span></span>|<span data-ttu-id="1b904-105">219</span><span class="sxs-lookup"><span data-stu-id="1b904-105">219</span></span>|  
|<span data-ttu-id="1b904-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="1b904-106">Keywords</span></span>|<span data-ttu-id="1b904-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1b904-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1b904-108">レベル</span><span class="sxs-lookup"><span data-stu-id="1b904-108">Level</span></span>|<span data-ttu-id="1b904-109">Error</span><span class="sxs-lookup"><span data-stu-id="1b904-109">Error</span></span>|  
|<span data-ttu-id="1b904-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1b904-110">Channel</span></span>|<span data-ttu-id="1b904-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1b904-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1b904-112">説明</span><span class="sxs-lookup"><span data-stu-id="1b904-112">Description</span></span>  
 <span data-ttu-id="1b904-113">このイベントは、WCF サービスがハンドルされない例外を検出した場合に生成されます。</span><span class="sxs-lookup"><span data-stu-id="1b904-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="1b904-114">これには、アクティベーション中のハンドルされない例外、メッセージ処理中のハンドルされない例外、およびユーザー コード内でのハンドルされない例外が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1b904-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1b904-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="1b904-115">Message</span></span>  
 <span data-ttu-id="1b904-116">メッセージの処理中に種類 '%2' のハンドルされない例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="1b904-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="1b904-117">完全な例外 ToString: %1。</span><span class="sxs-lookup"><span data-stu-id="1b904-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1b904-118">詳細</span><span class="sxs-lookup"><span data-stu-id="1b904-118">Details</span></span>  
  
|<span data-ttu-id="1b904-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1b904-119">Data Item Name</span></span>|<span data-ttu-id="1b904-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1b904-120">Data Item Type</span></span>|<span data-ttu-id="1b904-121">説明</span><span class="sxs-lookup"><span data-stu-id="1b904-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1b904-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="1b904-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="1b904-123">CLR 例外に対して `ToString`() を呼び出した結果。</span><span class="sxs-lookup"><span data-stu-id="1b904-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="1b904-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="1b904-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="1b904-125">例外の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="1b904-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="1b904-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="1b904-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="1b904-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="1b904-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1b904-128">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="1b904-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1b904-129">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="1b904-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1b904-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1b904-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1b904-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1b904-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
