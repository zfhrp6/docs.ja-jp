---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 7531cf27aec0ea9a71ee7b1906e8f7cee151695f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485955"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="75c0d-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="75c0d-102">ServiceTimeoutsBehavior</span></span>
<span data-ttu-id="75c0d-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="75c0d-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c0d-104">構文</span><span class="sxs-lookup"><span data-stu-id="75c0d-104">Syntax</span></span>  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="75c0d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="75c0d-105">Methods</span></span>  
 <span data-ttu-id="75c0d-106">ServiceTimeoutsBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="75c0d-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="75c0d-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="75c0d-107">Properties</span></span>  
 <span data-ttu-id="75c0d-108">ServiceTimeoutsBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="75c0d-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="75c0d-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="75c0d-109">TransactionTimeout</span></span>  
 <span data-ttu-id="75c0d-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="75c0d-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="75c0d-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="75c0d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75c0d-112">トランザクションを完了しなければならない期間。</span><span class="sxs-lookup"><span data-stu-id="75c0d-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75c0d-113">要件</span><span class="sxs-lookup"><span data-stu-id="75c0d-113">Requirements</span></span>  
  
|<span data-ttu-id="75c0d-114">MOF</span><span class="sxs-lookup"><span data-stu-id="75c0d-114">MOF</span></span>|<span data-ttu-id="75c0d-115">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="75c0d-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="75c0d-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="75c0d-116">Namespace</span></span>|<span data-ttu-id="75c0d-117">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="75c0d-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75c0d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="75c0d-118">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
