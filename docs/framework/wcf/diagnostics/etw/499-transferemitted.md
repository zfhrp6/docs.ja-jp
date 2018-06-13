---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469509"
---
# <a name="499---transferemitted"></a><span data-ttu-id="fff95-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="fff95-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="fff95-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fff95-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fff95-104">ID</span><span class="sxs-lookup"><span data-stu-id="fff95-104">ID</span></span>|<span data-ttu-id="fff95-105">499</span><span class="sxs-lookup"><span data-stu-id="fff95-105">499</span></span>|  
|<span data-ttu-id="fff95-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="fff95-106">Keywords</span></span>|<span data-ttu-id="fff95-107">Troubleshooting、UserEvents、EndToEndMonitoring、ServiceModel、WFTracking、ServiceHost、WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="fff95-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="fff95-108">レベル</span><span class="sxs-lookup"><span data-stu-id="fff95-108">Level</span></span>|<span data-ttu-id="fff95-109">LogAlways (常にログ)</span><span class="sxs-lookup"><span data-stu-id="fff95-109">LogAlways</span></span>|  
|<span data-ttu-id="fff95-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="fff95-110">Channel</span></span>|<span data-ttu-id="fff95-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="fff95-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fff95-112">説明</span><span class="sxs-lookup"><span data-stu-id="fff95-112">Description</span></span>  
 <span data-ttu-id="fff95-113">このイベントは、転送イベントが発生したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="fff95-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fff95-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="fff95-114">Message</span></span>  
 <span data-ttu-id="fff95-115">転送イベントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="fff95-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fff95-116">説明</span><span class="sxs-lookup"><span data-stu-id="fff95-116">Details</span></span>  
  
|<span data-ttu-id="fff95-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fff95-117">Data Item Name</span></span>|<span data-ttu-id="fff95-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fff95-118">Data Item Type</span></span>|<span data-ttu-id="fff95-119">説明</span><span class="sxs-lookup"><span data-stu-id="fff95-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fff95-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="fff95-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="fff95-121">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="fff95-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fff95-122">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="fff95-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fff95-123">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="fff95-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fff95-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fff95-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fff95-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fff95-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
