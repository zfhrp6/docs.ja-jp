---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460516"
---
# <a name="219---serviceexception"></a><span data-ttu-id="a6c02-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="a6c02-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="a6c02-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a6c02-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6c02-104">ID</span><span class="sxs-lookup"><span data-stu-id="a6c02-104">ID</span></span>|<span data-ttu-id="a6c02-105">219</span><span class="sxs-lookup"><span data-stu-id="a6c02-105">219</span></span>|  
|<span data-ttu-id="a6c02-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="a6c02-106">Keywords</span></span>|<span data-ttu-id="a6c02-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a6c02-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a6c02-108">レベル</span><span class="sxs-lookup"><span data-stu-id="a6c02-108">Level</span></span>|<span data-ttu-id="a6c02-109">Error</span><span class="sxs-lookup"><span data-stu-id="a6c02-109">Error</span></span>|  
|<span data-ttu-id="a6c02-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a6c02-110">Channel</span></span>|<span data-ttu-id="a6c02-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a6c02-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a6c02-112">説明</span><span class="sxs-lookup"><span data-stu-id="a6c02-112">Description</span></span>  
 <span data-ttu-id="a6c02-113">このイベントは、WCF サービスがハンドルされない例外を検出した場合に生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6c02-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="a6c02-114">これには、アクティベーション中のハンドルされない例外、メッセージ処理中のハンドルされない例外、およびユーザー コード内でのハンドルされない例外が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6c02-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a6c02-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="a6c02-115">Message</span></span>  
 <span data-ttu-id="a6c02-116">メッセージの処理中に種類 '%2' のハンドルされない例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="a6c02-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="a6c02-117">完全な例外 ToString: %1。</span><span class="sxs-lookup"><span data-stu-id="a6c02-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a6c02-118">説明</span><span class="sxs-lookup"><span data-stu-id="a6c02-118">Details</span></span>  
  
|<span data-ttu-id="a6c02-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a6c02-119">Data Item Name</span></span>|<span data-ttu-id="a6c02-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a6c02-120">Data Item Type</span></span>|<span data-ttu-id="a6c02-121">説明</span><span class="sxs-lookup"><span data-stu-id="a6c02-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a6c02-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="a6c02-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="a6c02-123">CLR 例外に対して `ToString`() を呼び出した結果。</span><span class="sxs-lookup"><span data-stu-id="a6c02-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="a6c02-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="a6c02-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="a6c02-125">例外の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="a6c02-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="a6c02-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="a6c02-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="a6c02-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="a6c02-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a6c02-128">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="a6c02-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a6c02-129">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="a6c02-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a6c02-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a6c02-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a6c02-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a6c02-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
