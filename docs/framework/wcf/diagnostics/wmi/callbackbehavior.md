---
title: CallbackBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5387e197cdf26a393ba23fd5696eb095dfd17a70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="cd436-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="cd436-102">CallbackBehavior</span></span>
<span data-ttu-id="cd436-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="cd436-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd436-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd436-104">Syntax</span></span>  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cd436-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cd436-105">Methods</span></span>  
 <span data-ttu-id="cd436-106">CallbackBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="cd436-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cd436-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cd436-107">Properties</span></span>  
 <span data-ttu-id="cd436-108">CallbackBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="cd436-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="cd436-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="cd436-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="cd436-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="cd436-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd436-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd436-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd436-112">true の場合、サービスが双方向セッションを閉じると、セッションが自動的に閉じられます。</span><span class="sxs-lookup"><span data-stu-id="cd436-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="cd436-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="cd436-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="cd436-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="cd436-114">Data type: string</span></span>  
<span data-ttu-id="cd436-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd436-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd436-116">サービスが単一のスレッド、複数のスレッド、再入可能呼び出しのいずれをサポートするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd436-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="cd436-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="cd436-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="cd436-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="cd436-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd436-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd436-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd436-120">不明なシリアル化データをネットワークで送信するかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="cd436-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="cd436-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="cd436-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="cd436-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="cd436-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd436-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd436-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd436-124">有効にした場合は、コールバックの例外に関する詳細情報が、サービスに戻されるエラーに添付されます。</span><span class="sxs-lookup"><span data-stu-id="cd436-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="cd436-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="cd436-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="cd436-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="cd436-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd436-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd436-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd436-128">1 つのシリアル化されたオブジェクトで許可される項目の最大数。</span><span class="sxs-lookup"><span data-stu-id="cd436-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="cd436-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="cd436-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="cd436-130">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="cd436-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd436-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd436-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd436-132">現在の同期コンテキストを使用して実行のスレッドを選択するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd436-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="cd436-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="cd436-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="cd436-134">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="cd436-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd436-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cd436-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd436-136">システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd436-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd436-137">必要条件</span><span class="sxs-lookup"><span data-stu-id="cd436-137">Requirements</span></span>  
  
|<span data-ttu-id="cd436-138">MOF</span><span class="sxs-lookup"><span data-stu-id="cd436-138">MOF</span></span>|<span data-ttu-id="cd436-139">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="cd436-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cd436-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="cd436-140">Namespace</span></span>|<span data-ttu-id="cd436-141">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="cd436-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd436-142">参照</span><span class="sxs-lookup"><span data-stu-id="cd436-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
