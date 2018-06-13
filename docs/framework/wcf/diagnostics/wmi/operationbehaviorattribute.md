---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 4f731d146885265d9f956c182f1bebdba5db924b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486872"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="3adbd-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="3adbd-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="3adbd-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="3adbd-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3adbd-104">構文</span><span class="sxs-lookup"><span data-stu-id="3adbd-104">Syntax</span></span>  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3adbd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3adbd-105">Methods</span></span>  
 <span data-ttu-id="3adbd-106">OperationBehaviorAttribute クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="3adbd-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3adbd-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3adbd-107">Properties</span></span>  
 <span data-ttu-id="3adbd-108">OperationBehaviorAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3adbd-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="3adbd-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="3adbd-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="3adbd-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3adbd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="3adbd-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3adbd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3adbd-112">パラメーターの自動破棄機能の状態です。</span><span class="sxs-lookup"><span data-stu-id="3adbd-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="3adbd-113">偽装</span><span class="sxs-lookup"><span data-stu-id="3adbd-113">Impersonation</span></span>  
 <span data-ttu-id="3adbd-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3adbd-114">Data type: string</span></span>  
  
 <span data-ttu-id="3adbd-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3adbd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3adbd-116">操作がサポートする、呼び出し元の偽装レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3adbd-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="3adbd-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="3adbd-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="3adbd-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="3adbd-118">Data type: string</span></span>  
  
 <span data-ttu-id="3adbd-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3adbd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3adbd-120">操作の呼び出し過程のどの時点でオブジェクトをリサイクルするかを示します。</span><span class="sxs-lookup"><span data-stu-id="3adbd-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="3adbd-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="3adbd-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="3adbd-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3adbd-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3adbd-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3adbd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3adbd-124">未処理の例外が発生しなかった場合に、現在のトランザクションを自動的にコミットするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3adbd-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="3adbd-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="3adbd-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="3adbd-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3adbd-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="3adbd-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3adbd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3adbd-128">操作がトランザクションを必要とするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3adbd-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3adbd-129">要件</span><span class="sxs-lookup"><span data-stu-id="3adbd-129">Requirements</span></span>  
  
|<span data-ttu-id="3adbd-130">MOF</span><span class="sxs-lookup"><span data-stu-id="3adbd-130">MOF</span></span>|<span data-ttu-id="3adbd-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="3adbd-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3adbd-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="3adbd-132">Namespace</span></span>|<span data-ttu-id="3adbd-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="3adbd-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3adbd-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3adbd-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
