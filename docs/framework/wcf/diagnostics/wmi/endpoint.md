---
title: エンドポイント
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 5d597e9e029cec3552c94b47a64dfbf36d933e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487647"
---
# <a name="endpoint"></a><span data-ttu-id="51072-102">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="51072-102">Endpoint</span></span>
<span data-ttu-id="51072-103">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="51072-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51072-104">構文</span><span class="sxs-lookup"><span data-stu-id="51072-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="51072-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="51072-105">Methods</span></span>  
 <span data-ttu-id="51072-106">Endpoint クラスは次のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="51072-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="51072-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="51072-107">Method</span></span>|<span data-ttu-id="51072-108">説明</span><span class="sxs-lookup"><span data-stu-id="51072-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51072-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="51072-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="51072-110">操作パフォーマンス カウンターのインスタンスの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="51072-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="51072-111">プロパティ</span><span class="sxs-lookup"><span data-stu-id="51072-111">Properties</span></span>  
 <span data-ttu-id="51072-112">Endpoint クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="51072-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="51072-113">Address</span><span class="sxs-lookup"><span data-stu-id="51072-113">Address</span></span>  
 <span data-ttu-id="51072-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="51072-114">Data type: string</span></span>  
  
 <span data-ttu-id="51072-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-116">エンドポイントのアドレスを格納している URI。</span><span class="sxs-lookup"><span data-stu-id="51072-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="51072-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="51072-117">AddressHeaders</span></span>  
 <span data-ttu-id="51072-118">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="51072-118">Data type: string array</span></span>  
  
 <span data-ttu-id="51072-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-120">このエンドポイントに接続しているアドレス ヘッダーのコレクション</span><span class="sxs-lookup"><span data-stu-id="51072-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="51072-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="51072-121">AddressIdentity</span></span>  
 <span data-ttu-id="51072-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="51072-122">Data type: string</span></span>  
  
 <span data-ttu-id="51072-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-124">エンドポイントの ID</span><span class="sxs-lookup"><span data-stu-id="51072-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="51072-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="51072-125">AppDomainId</span></span>  
 <span data-ttu-id="51072-126">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="51072-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="51072-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-128">エンドポイントをホストする appdomain の appdomain ID</span><span class="sxs-lookup"><span data-stu-id="51072-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="51072-129">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="51072-129">Behaviors</span></span>  
 <span data-ttu-id="51072-130">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="51072-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="51072-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-132">このエンドポイントが実装する動作のコレクション</span><span class="sxs-lookup"><span data-stu-id="51072-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="51072-133">バインディング</span><span class="sxs-lookup"><span data-stu-id="51072-133">Binding</span></span>  
 <span data-ttu-id="51072-134">データ型 : Binding</span><span class="sxs-lookup"><span data-stu-id="51072-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="51072-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-136">このエンドポイントが使用するバインディング</span><span class="sxs-lookup"><span data-stu-id="51072-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="51072-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="51072-137">ContractName</span></span>  
 <span data-ttu-id="51072-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="51072-138">Data type: string</span></span>  
  
 <span data-ttu-id="51072-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-140">このエンドポイントが公開するコントラクトを指定する文字列</span><span class="sxs-lookup"><span data-stu-id="51072-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="51072-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="51072-141">CounterInstanceName</span></span>  
 <span data-ttu-id="51072-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="51072-142">Data type: string</span></span>  
  
 <span data-ttu-id="51072-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-144">エンドポイントのパフォーマンス カウンターのインスタンス名</span><span class="sxs-lookup"><span data-stu-id="51072-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="51072-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="51072-145">ListenUri</span></span>  
 <span data-ttu-id="51072-146">データ型: string</span><span class="sxs-lookup"><span data-stu-id="51072-146">Data type: string</span></span>  
  
 <span data-ttu-id="51072-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-148">エンドポイントがリッスンする URI</span><span class="sxs-lookup"><span data-stu-id="51072-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="51072-149">名前</span><span class="sxs-lookup"><span data-stu-id="51072-149">Name</span></span>  
 <span data-ttu-id="51072-150">データ型: string</span><span class="sxs-lookup"><span data-stu-id="51072-150">Data type: string</span></span>  
  
 <span data-ttu-id="51072-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-152">このエンドポイントの一意の名前</span><span class="sxs-lookup"><span data-stu-id="51072-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="51072-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="51072-153">ProcessId</span></span>  
 <span data-ttu-id="51072-154">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="51072-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="51072-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-156">エンドポイントをホストするプロセスのプロセス ID</span><span class="sxs-lookup"><span data-stu-id="51072-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="51072-157">ref</span><span class="sxs-lookup"><span data-stu-id="51072-157">ref</span></span>  
 <span data-ttu-id="51072-158">データ型 : Contract</span><span class="sxs-lookup"><span data-stu-id="51072-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="51072-159">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="51072-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51072-160">このエンドポイントが公開しているコントラクト。</span><span class="sxs-lookup"><span data-stu-id="51072-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51072-161">要件</span><span class="sxs-lookup"><span data-stu-id="51072-161">Requirements</span></span>  
  
|<span data-ttu-id="51072-162">MOF</span><span class="sxs-lookup"><span data-stu-id="51072-162">MOF</span></span>|<span data-ttu-id="51072-163">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="51072-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="51072-164">Namespace</span><span class="sxs-lookup"><span data-stu-id="51072-164">Namespace</span></span>|<span data-ttu-id="51072-165">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="51072-165">Defined in root\ServiceModel</span></span>|
