---
title: 2578 - TryCatchExceptionFromCatchOrFinally
ms.date: 03/30/2017
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
ms.openlocfilehash: 46fb52e665d49ed7a0336dbeeb6ed07f0d479fb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511528"
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a><span data-ttu-id="259eb-102">2578 - TryCatchExceptionFromCatchOrFinally</span><span class="sxs-lookup"><span data-stu-id="259eb-102">2578 - TryCatchExceptionFromCatchOrFinally</span></span>
## <a name="properties"></a><span data-ttu-id="259eb-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="259eb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="259eb-104">ID</span><span class="sxs-lookup"><span data-stu-id="259eb-104">ID</span></span>|<span data-ttu-id="259eb-105">2578</span><span class="sxs-lookup"><span data-stu-id="259eb-105">2578</span></span>|  
|<span data-ttu-id="259eb-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="259eb-106">Keywords</span></span>|<span data-ttu-id="259eb-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="259eb-107">WFActivities</span></span>|  
|<span data-ttu-id="259eb-108">レベル</span><span class="sxs-lookup"><span data-stu-id="259eb-108">Level</span></span>|<span data-ttu-id="259eb-109">警告</span><span class="sxs-lookup"><span data-stu-id="259eb-109">Warning</span></span>|  
|<span data-ttu-id="259eb-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="259eb-110">Channel</span></span>|<span data-ttu-id="259eb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="259eb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="259eb-112">説明</span><span class="sxs-lookup"><span data-stu-id="259eb-112">Description</span></span>  
 <span data-ttu-id="259eb-113">Catch または Finally アクティビティから例外がスローされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="259eb-113">Indicates a Catch or Finally activity has thrown an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="259eb-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="259eb-114">Message</span></span>  
 <span data-ttu-id="259eb-115">TryCatch アクティビティ '%1' に関連付けられている Catch または Finally アクティビティは例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="259eb-115">A Catch or Finally activity that is associated with the TryCatch activity '%1' has thrown an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="259eb-116">詳細</span><span class="sxs-lookup"><span data-stu-id="259eb-116">Details</span></span>  
  
|<span data-ttu-id="259eb-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="259eb-117">Data Item Name</span></span>|<span data-ttu-id="259eb-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="259eb-118">Data Item Type</span></span>|<span data-ttu-id="259eb-119">説明</span><span class="sxs-lookup"><span data-stu-id="259eb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="259eb-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="259eb-120">DisplayName</span></span>|<span data-ttu-id="259eb-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="259eb-121">xs:string</span></span>|<span data-ttu-id="259eb-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="259eb-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="259eb-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="259eb-123">AppDomain</span></span>|<span data-ttu-id="259eb-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="259eb-124">xs:string</span></span>|<span data-ttu-id="259eb-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="259eb-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
