---
title: 207 - FaultProviderInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fe3698653be04119c84c5f423207458e9d033dc1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="10ab5-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="10ab5-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="10ab5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="10ab5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10ab5-104">ID</span><span class="sxs-lookup"><span data-stu-id="10ab5-104">ID</span></span>|<span data-ttu-id="10ab5-105">207</span><span class="sxs-lookup"><span data-stu-id="10ab5-105">207</span></span>|  
|<span data-ttu-id="10ab5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="10ab5-106">Keywords</span></span>|<span data-ttu-id="10ab5-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="10ab5-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="10ab5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="10ab5-108">Level</span></span>|<span data-ttu-id="10ab5-109">情報</span><span class="sxs-lookup"><span data-stu-id="10ab5-109">Information</span></span>|  
|<span data-ttu-id="10ab5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="10ab5-110">Channel</span></span>|<span data-ttu-id="10ab5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="10ab5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="10ab5-112">説明</span><span class="sxs-lookup"><span data-stu-id="10ab5-112">Description</span></span>  
 <span data-ttu-id="10ab5-113">このイベントは、`FaultProvider` が呼び出された後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="10ab5-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="10ab5-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="10ab5-114">Message</span></span>  
 <span data-ttu-id="10ab5-115">ディスパッチャーが型 '%1' の FaultProvider を呼び出し、種類 '%2' の例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="10ab5-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="10ab5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="10ab5-116">Details</span></span>  
  
|<span data-ttu-id="10ab5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="10ab5-117">Data Item Name</span></span>|<span data-ttu-id="10ab5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="10ab5-118">Data Item Type</span></span>|<span data-ttu-id="10ab5-119">説明</span><span class="sxs-lookup"><span data-stu-id="10ab5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="10ab5-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="10ab5-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="10ab5-121">呼び出された `FaultProvider` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="10ab5-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="10ab5-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="10ab5-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="10ab5-123">`FaultProvider` の操作対象である例外の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="10ab5-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="10ab5-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="10ab5-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="10ab5-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="10ab5-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="10ab5-126">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="10ab5-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="10ab5-127">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="10ab5-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="10ab5-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="10ab5-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="10ab5-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="10ab5-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
