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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9df9629e280a2aec6acf93773e09384e763280ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="1830a-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="1830a-102">CallbackBehavior</span></span>
<span data-ttu-id="1830a-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="1830a-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1830a-104">構文</span><span class="sxs-lookup"><span data-stu-id="1830a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1830a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1830a-105">Methods</span></span>  
 <span data-ttu-id="1830a-106">CallbackBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="1830a-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1830a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1830a-107">Properties</span></span>  
 <span data-ttu-id="1830a-108">CallbackBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="1830a-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="1830a-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="1830a-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="1830a-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1830a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="1830a-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1830a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1830a-112">true の場合、サービスが双方向セッションを閉じると、セッションが自動的に閉じられます。</span><span class="sxs-lookup"><span data-stu-id="1830a-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="1830a-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="1830a-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="1830a-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="1830a-114">Data type: string</span></span>  
<span data-ttu-id="1830a-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1830a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1830a-116">サービスが単一のスレッド、複数のスレッド、再入可能呼び出しのいずれをサポートするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1830a-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="1830a-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="1830a-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="1830a-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1830a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1830a-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1830a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1830a-120">不明なシリアル化データをネットワークで送信するかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="1830a-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="1830a-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="1830a-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="1830a-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1830a-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1830a-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1830a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1830a-124">有効にした場合は、コールバックの例外に関する詳細情報が、サービスに戻されるエラーに添付されます。</span><span class="sxs-lookup"><span data-stu-id="1830a-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="1830a-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="1830a-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="1830a-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1830a-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="1830a-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1830a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1830a-128">1 つのシリアル化されたオブジェクトで許可される項目の最大数。</span><span class="sxs-lookup"><span data-stu-id="1830a-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="1830a-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="1830a-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="1830a-130">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1830a-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="1830a-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1830a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1830a-132">現在の同期コンテキストを使用して実行のスレッドを選択するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1830a-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="1830a-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="1830a-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="1830a-134">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1830a-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="1830a-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1830a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1830a-136">システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1830a-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1830a-137">要件</span><span class="sxs-lookup"><span data-stu-id="1830a-137">Requirements</span></span>  
  
|<span data-ttu-id="1830a-138">MOF</span><span class="sxs-lookup"><span data-stu-id="1830a-138">MOF</span></span>|<span data-ttu-id="1830a-139">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="1830a-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1830a-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="1830a-140">Namespace</span></span>|<span data-ttu-id="1830a-141">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="1830a-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1830a-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="1830a-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
