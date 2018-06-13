---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484189"
---
# <a name="activitytransfer"></a><span data-ttu-id="da014-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="da014-102">ActivityTransfer</span></span>
<span data-ttu-id="da014-103">アクティビティ転送イベント</span><span class="sxs-lookup"><span data-stu-id="da014-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da014-104">構文</span><span class="sxs-lookup"><span data-stu-id="da014-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="da014-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="da014-105">Methods</span></span>  
 <span data-ttu-id="da014-106">ActivityTransfer クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="da014-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="da014-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="da014-107">Properties</span></span>  
 <span data-ttu-id="da014-108">ActivityTransfer クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="da014-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="da014-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="da014-109">ActivityID</span></span>  
  
-   <span data-ttu-id="da014-110">データ型: object</span><span class="sxs-lookup"><span data-stu-id="da014-110">Data type: object</span></span>  
    <span data-ttu-id="da014-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="da014-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="da014-112">アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="da014-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="da014-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="da014-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="da014-114">データ型: object</span><span class="sxs-lookup"><span data-stu-id="da014-114">Data type: object</span></span>  
    <span data-ttu-id="da014-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="da014-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="da014-116">関連アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="da014-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da014-117">要件</span><span class="sxs-lookup"><span data-stu-id="da014-117">Requirements</span></span>  
  
|<span data-ttu-id="da014-118">MOF</span><span class="sxs-lookup"><span data-stu-id="da014-118">MOF</span></span>|<span data-ttu-id="da014-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="da014-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="da014-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="da014-120">Namespace</span></span>|<span data-ttu-id="da014-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="da014-121">Defined in root\ServiceModel.</span></span>|
