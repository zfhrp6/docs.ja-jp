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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f3db50a32fabc117c79eef5ac086a7798f86ed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="ab47a-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="ab47a-102">ActivityTransfer</span></span>
<span data-ttu-id="ab47a-103">アクティビティ転送イベント</span><span class="sxs-lookup"><span data-stu-id="ab47a-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab47a-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab47a-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ab47a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ab47a-105">Methods</span></span>  
 <span data-ttu-id="ab47a-106">ActivityTransfer クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="ab47a-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab47a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ab47a-107">Properties</span></span>  
 <span data-ttu-id="ab47a-108">ActivityTransfer クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ab47a-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="ab47a-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="ab47a-109">ActivityID</span></span>  
  
-   <span data-ttu-id="ab47a-110">データ型: object</span><span class="sxs-lookup"><span data-stu-id="ab47a-110">Data type: object</span></span>  
    <span data-ttu-id="ab47a-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ab47a-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="ab47a-112">アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="ab47a-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="ab47a-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="ab47a-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="ab47a-114">データ型: object</span><span class="sxs-lookup"><span data-stu-id="ab47a-114">Data type: object</span></span>  
    <span data-ttu-id="ab47a-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ab47a-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="ab47a-116">関連アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="ab47a-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab47a-117">要件</span><span class="sxs-lookup"><span data-stu-id="ab47a-117">Requirements</span></span>  
  
|<span data-ttu-id="ab47a-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ab47a-118">MOF</span></span>|<span data-ttu-id="ab47a-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ab47a-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ab47a-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="ab47a-120">Namespace</span></span>|<span data-ttu-id="ab47a-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ab47a-121">Defined in root\ServiceModel.</span></span>|
