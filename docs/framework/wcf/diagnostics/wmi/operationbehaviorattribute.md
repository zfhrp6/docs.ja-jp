---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da0bc2ac9a4283ec9b23a1d4767f664de071ef47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="4aecd-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="4aecd-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="4aecd-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="4aecd-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aecd-104">構文</span><span class="sxs-lookup"><span data-stu-id="4aecd-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4aecd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4aecd-105">Methods</span></span>  
 <span data-ttu-id="4aecd-106">OperationBehaviorAttribute クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="4aecd-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4aecd-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4aecd-107">Properties</span></span>  
 <span data-ttu-id="4aecd-108">OperationBehaviorAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="4aecd-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="4aecd-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="4aecd-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="4aecd-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="4aecd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="4aecd-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4aecd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aecd-112">パラメーターの自動破棄機能の状態です。</span><span class="sxs-lookup"><span data-stu-id="4aecd-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="4aecd-113">偽装</span><span class="sxs-lookup"><span data-stu-id="4aecd-113">Impersonation</span></span>  
 <span data-ttu-id="4aecd-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="4aecd-114">Data type: string</span></span>  
  
 <span data-ttu-id="4aecd-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4aecd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aecd-116">操作がサポートする、呼び出し元の偽装レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4aecd-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="4aecd-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="4aecd-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="4aecd-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="4aecd-118">Data type: string</span></span>  
  
 <span data-ttu-id="4aecd-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4aecd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aecd-120">操作の呼び出し過程のどの時点でオブジェクトをリサイクルするかを示します。</span><span class="sxs-lookup"><span data-stu-id="4aecd-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="4aecd-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="4aecd-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="4aecd-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="4aecd-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="4aecd-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4aecd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aecd-124">未処理の例外が発生しなかった場合に、現在のトランザクションを自動的にコミットするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4aecd-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="4aecd-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="4aecd-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="4aecd-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="4aecd-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="4aecd-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4aecd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aecd-128">操作がトランザクションを必要とするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4aecd-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aecd-129">要件</span><span class="sxs-lookup"><span data-stu-id="4aecd-129">Requirements</span></span>  
  
|<span data-ttu-id="4aecd-130">MOF</span><span class="sxs-lookup"><span data-stu-id="4aecd-130">MOF</span></span>|<span data-ttu-id="4aecd-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="4aecd-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4aecd-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="4aecd-132">Namespace</span></span>|<span data-ttu-id="4aecd-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="4aecd-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4aecd-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="4aecd-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
