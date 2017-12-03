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
ms.openlocfilehash: 7c10d9e26f86fa569b1a607c9b755f32ee97792a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="04d52-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="04d52-102">CallbackBehavior</span></span>
<span data-ttu-id="04d52-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="04d52-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04d52-104">構文</span><span class="sxs-lookup"><span data-stu-id="04d52-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="04d52-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="04d52-105">Methods</span></span>  
 <span data-ttu-id="04d52-106">CallbackBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="04d52-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="04d52-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="04d52-107">Properties</span></span>  
 <span data-ttu-id="04d52-108">CallbackBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="04d52-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="04d52-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="04d52-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="04d52-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="04d52-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="04d52-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04d52-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04d52-112">true の場合、サービスが双方向セッションを閉じると、セッションが自動的に閉じられます。</span><span class="sxs-lookup"><span data-stu-id="04d52-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="04d52-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="04d52-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="04d52-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="04d52-114">Data type: string</span></span>  
<span data-ttu-id="04d52-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04d52-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04d52-116">サービスが単一のスレッド、複数のスレッド、再入可能呼び出しのいずれをサポートするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="04d52-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="04d52-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="04d52-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="04d52-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="04d52-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="04d52-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04d52-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04d52-120">不明なシリアル化データをネットワークで送信するかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="04d52-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="04d52-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="04d52-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="04d52-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="04d52-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="04d52-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04d52-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04d52-124">有効にした場合は、コールバックの例外に関する詳細情報が、サービスに戻されるエラーに添付されます。</span><span class="sxs-lookup"><span data-stu-id="04d52-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="04d52-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="04d52-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="04d52-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="04d52-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="04d52-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04d52-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04d52-128">1 つのシリアル化されたオブジェクトで許可される項目の最大数。</span><span class="sxs-lookup"><span data-stu-id="04d52-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="04d52-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="04d52-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="04d52-130">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="04d52-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="04d52-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04d52-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04d52-132">現在の同期コンテキストを使用して実行のスレッドを選択するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="04d52-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="04d52-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="04d52-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="04d52-134">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="04d52-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="04d52-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="04d52-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04d52-136">システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="04d52-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d52-137">要件</span><span class="sxs-lookup"><span data-stu-id="04d52-137">Requirements</span></span>  
  
|<span data-ttu-id="04d52-138">MOF</span><span class="sxs-lookup"><span data-stu-id="04d52-138">MOF</span></span>|<span data-ttu-id="04d52-139">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="04d52-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="04d52-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="04d52-140">Namespace</span></span>|<span data-ttu-id="04d52-141">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="04d52-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04d52-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="04d52-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
