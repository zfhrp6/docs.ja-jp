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
ms.openlocfilehash: a65104a6fe76c22fca308091cc02e9496912129c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="51bb2-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="51bb2-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="51bb2-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="51bb2-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51bb2-104">構文</span><span class="sxs-lookup"><span data-stu-id="51bb2-104">Syntax</span></span>  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="51bb2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="51bb2-105">Methods</span></span>  
 <span data-ttu-id="51bb2-106">ServiceTimeoutsBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="51bb2-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="51bb2-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="51bb2-107">Properties</span></span>  
 <span data-ttu-id="51bb2-108">ServiceTimeoutsBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="51bb2-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="51bb2-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="51bb2-109">TransactionTimeout</span></span>  
 <span data-ttu-id="51bb2-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="51bb2-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="51bb2-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51bb2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51bb2-112">トランザクションを完了しなければならない期間。</span><span class="sxs-lookup"><span data-stu-id="51bb2-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51bb2-113">要件</span><span class="sxs-lookup"><span data-stu-id="51bb2-113">Requirements</span></span>  
  
|<span data-ttu-id="51bb2-114">MOF</span><span class="sxs-lookup"><span data-stu-id="51bb2-114">MOF</span></span>|<span data-ttu-id="51bb2-115">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="51bb2-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="51bb2-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="51bb2-116">Namespace</span></span>|<span data-ttu-id="51bb2-117">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="51bb2-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51bb2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="51bb2-118">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
