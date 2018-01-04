---
title: "エンドポイント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bcb02ae01d66830d9bfd486c5ae3941c45c2a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint"></a><span data-ttu-id="66013-102">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="66013-102">Endpoint</span></span>
<span data-ttu-id="66013-103">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="66013-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66013-104">構文</span><span class="sxs-lookup"><span data-stu-id="66013-104">Syntax</span></span>  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="66013-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="66013-105">Methods</span></span>  
 <span data-ttu-id="66013-106">Endpoint クラスは次のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="66013-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="66013-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="66013-107">Method</span></span>|<span data-ttu-id="66013-108">説明</span><span class="sxs-lookup"><span data-stu-id="66013-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66013-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="66013-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="66013-110">操作パフォーマンス カウンターのインスタンスの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="66013-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="66013-111">プロパティ</span><span class="sxs-lookup"><span data-stu-id="66013-111">Properties</span></span>  
 <span data-ttu-id="66013-112">Endpoint クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="66013-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="66013-113">Address</span><span class="sxs-lookup"><span data-stu-id="66013-113">Address</span></span>  
 <span data-ttu-id="66013-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="66013-114">Data type: string</span></span>  
  
 <span data-ttu-id="66013-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-116">エンドポイントのアドレスを格納している URI。</span><span class="sxs-lookup"><span data-stu-id="66013-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="66013-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="66013-117">AddressHeaders</span></span>  
 <span data-ttu-id="66013-118">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="66013-118">Data type: string array</span></span>  
  
 <span data-ttu-id="66013-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-120">このエンドポイントに接続しているアドレス ヘッダーのコレクション</span><span class="sxs-lookup"><span data-stu-id="66013-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="66013-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="66013-121">AddressIdentity</span></span>  
 <span data-ttu-id="66013-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="66013-122">Data type: string</span></span>  
  
 <span data-ttu-id="66013-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-124">エンドポイントの ID</span><span class="sxs-lookup"><span data-stu-id="66013-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="66013-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="66013-125">AppDomainId</span></span>  
 <span data-ttu-id="66013-126">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="66013-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="66013-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-128">エンドポイントをホストする appdomain の appdomain ID</span><span class="sxs-lookup"><span data-stu-id="66013-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="66013-129">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="66013-129">Behaviors</span></span>  
 <span data-ttu-id="66013-130">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="66013-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="66013-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-132">このエンドポイントが実装する動作のコレクション</span><span class="sxs-lookup"><span data-stu-id="66013-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="66013-133">バインディング</span><span class="sxs-lookup"><span data-stu-id="66013-133">Binding</span></span>  
 <span data-ttu-id="66013-134">データ型 : Binding</span><span class="sxs-lookup"><span data-stu-id="66013-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="66013-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-136">このエンドポイントが使用するバインディング</span><span class="sxs-lookup"><span data-stu-id="66013-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="66013-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="66013-137">ContractName</span></span>  
 <span data-ttu-id="66013-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="66013-138">Data type: string</span></span>  
  
 <span data-ttu-id="66013-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-140">このエンドポイントが公開するコントラクトを指定する文字列</span><span class="sxs-lookup"><span data-stu-id="66013-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="66013-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="66013-141">CounterInstanceName</span></span>  
 <span data-ttu-id="66013-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="66013-142">Data type: string</span></span>  
  
 <span data-ttu-id="66013-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-144">エンドポイントのパフォーマンス カウンターのインスタンス名</span><span class="sxs-lookup"><span data-stu-id="66013-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="66013-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="66013-145">ListenUri</span></span>  
 <span data-ttu-id="66013-146">データ型: string</span><span class="sxs-lookup"><span data-stu-id="66013-146">Data type: string</span></span>  
  
 <span data-ttu-id="66013-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-148">エンドポイントがリッスンする URI</span><span class="sxs-lookup"><span data-stu-id="66013-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="66013-149">名前</span><span class="sxs-lookup"><span data-stu-id="66013-149">Name</span></span>  
 <span data-ttu-id="66013-150">データ型: string</span><span class="sxs-lookup"><span data-stu-id="66013-150">Data type: string</span></span>  
  
 <span data-ttu-id="66013-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-152">このエンドポイントの一意の名前</span><span class="sxs-lookup"><span data-stu-id="66013-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="66013-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="66013-153">ProcessId</span></span>  
 <span data-ttu-id="66013-154">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="66013-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="66013-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-156">エンドポイントをホストするプロセスのプロセス ID</span><span class="sxs-lookup"><span data-stu-id="66013-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="66013-157">ref</span><span class="sxs-lookup"><span data-stu-id="66013-157">ref</span></span>  
 <span data-ttu-id="66013-158">データ型 : Contract</span><span class="sxs-lookup"><span data-stu-id="66013-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="66013-159">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="66013-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66013-160">このエンドポイントが公開しているコントラクト。</span><span class="sxs-lookup"><span data-stu-id="66013-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66013-161">要件</span><span class="sxs-lookup"><span data-stu-id="66013-161">Requirements</span></span>  
  
|<span data-ttu-id="66013-162">MOF</span><span class="sxs-lookup"><span data-stu-id="66013-162">MOF</span></span>|<span data-ttu-id="66013-163">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="66013-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="66013-164">Namespace</span><span class="sxs-lookup"><span data-stu-id="66013-164">Namespace</span></span>|<span data-ttu-id="66013-165">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="66013-165">Defined in root\ServiceModel</span></span>|
