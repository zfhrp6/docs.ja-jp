---
title: ServiceTimeoutsBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4828b9a6b20c11f1f234f0ef521686164c7f8c66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="b9b47-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="b9b47-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="b9b47-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="b9b47-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b47-104">構文</span><span class="sxs-lookup"><span data-stu-id="b9b47-104">Syntax</span></span>  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b9b47-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b9b47-105">Methods</span></span>  
 <span data-ttu-id="b9b47-106">ServiceTimeoutsBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="b9b47-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b9b47-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b9b47-107">Properties</span></span>  
 <span data-ttu-id="b9b47-108">ServiceTimeoutsBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b9b47-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="b9b47-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="b9b47-109">TransactionTimeout</span></span>  
 <span data-ttu-id="b9b47-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="b9b47-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="b9b47-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b9b47-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b9b47-112">トランザクションを完了しなければならない期間。</span><span class="sxs-lookup"><span data-stu-id="b9b47-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b47-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="b9b47-113">Requirements</span></span>  
  
|<span data-ttu-id="b9b47-114">MOF</span><span class="sxs-lookup"><span data-stu-id="b9b47-114">MOF</span></span>|<span data-ttu-id="b9b47-115">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="b9b47-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b9b47-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="b9b47-116">Namespace</span></span>|<span data-ttu-id="b9b47-117">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="b9b47-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9b47-118">参照</span><span class="sxs-lookup"><span data-stu-id="b9b47-118">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
