---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acbc346da940caf933868a03295744132bda4733
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="69bbc-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="69bbc-102">ActivityTransfer</span></span>
<span data-ttu-id="69bbc-103">アクティビティ転送イベント</span><span class="sxs-lookup"><span data-stu-id="69bbc-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69bbc-104">構文</span><span class="sxs-lookup"><span data-stu-id="69bbc-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="69bbc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="69bbc-105">Methods</span></span>  
 <span data-ttu-id="69bbc-106">ActivityTransfer クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="69bbc-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="69bbc-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="69bbc-107">Properties</span></span>  
 <span data-ttu-id="69bbc-108">ActivityTransfer クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="69bbc-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="69bbc-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="69bbc-109">ActivityID</span></span>  
  
-   <span data-ttu-id="69bbc-110">データ型: object</span><span class="sxs-lookup"><span data-stu-id="69bbc-110">Data type: object</span></span>  
    <span data-ttu-id="69bbc-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="69bbc-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="69bbc-112">アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="69bbc-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="69bbc-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="69bbc-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="69bbc-114">データ型: object</span><span class="sxs-lookup"><span data-stu-id="69bbc-114">Data type: object</span></span>  
    <span data-ttu-id="69bbc-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="69bbc-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="69bbc-116">関連アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="69bbc-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69bbc-117">要件</span><span class="sxs-lookup"><span data-stu-id="69bbc-117">Requirements</span></span>  
  
|<span data-ttu-id="69bbc-118">MOF</span><span class="sxs-lookup"><span data-stu-id="69bbc-118">MOF</span></span>|<span data-ttu-id="69bbc-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="69bbc-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="69bbc-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="69bbc-120">Namespace</span></span>|<span data-ttu-id="69bbc-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="69bbc-121">Defined in root\ServiceModel.</span></span>|
