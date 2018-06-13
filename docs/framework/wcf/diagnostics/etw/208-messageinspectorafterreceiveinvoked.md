---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 3499131fcb52f0a0ab6d0e78e165522b7092612f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458899"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="2002e-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="2002e-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="2002e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2002e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2002e-104">ID</span><span class="sxs-lookup"><span data-stu-id="2002e-104">ID</span></span>|<span data-ttu-id="2002e-105">208</span><span class="sxs-lookup"><span data-stu-id="2002e-105">208</span></span>|  
|<span data-ttu-id="2002e-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2002e-106">Keywords</span></span>|<span data-ttu-id="2002e-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2002e-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2002e-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2002e-108">Level</span></span>|<span data-ttu-id="2002e-109">情報</span><span class="sxs-lookup"><span data-stu-id="2002e-109">Information</span></span>|  
|<span data-ttu-id="2002e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2002e-110">Channel</span></span>|<span data-ttu-id="2002e-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2002e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2002e-112">説明</span><span class="sxs-lookup"><span data-stu-id="2002e-112">Description</span></span>  
 <span data-ttu-id="2002e-113">このイベントは、メッセージ インスペクターで Service Model が `AfterReceive` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="2002e-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2002e-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2002e-114">Message</span></span>  
 <span data-ttu-id="2002e-115">ディスパッチャーが型 '%1' の MessageInspector で 'AfterReceiveReply' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="2002e-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2002e-116">詳細</span><span class="sxs-lookup"><span data-stu-id="2002e-116">Details</span></span>  
  
|<span data-ttu-id="2002e-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2002e-117">Data Item Name</span></span>|<span data-ttu-id="2002e-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2002e-118">Data Item Type</span></span>|<span data-ttu-id="2002e-119">説明</span><span class="sxs-lookup"><span data-stu-id="2002e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2002e-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="2002e-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="2002e-121">呼び出された `MessageInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="2002e-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="2002e-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="2002e-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="2002e-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="2002e-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2002e-124">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="2002e-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2002e-125">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="2002e-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2002e-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2002e-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2002e-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2002e-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
