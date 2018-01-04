---
title: "サービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7b631ede7bd011a92003dc5f6083c1c427d990e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="service"></a><span data-ttu-id="7b7be-102">サービス</span><span class="sxs-lookup"><span data-stu-id="7b7be-102">Service</span></span>
<span data-ttu-id="7b7be-103">サービス</span><span class="sxs-lookup"><span data-stu-id="7b7be-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b7be-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b7be-104">Syntax</span></span>  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7b7be-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7b7be-105">Methods</span></span>  
 <span data-ttu-id="7b7be-106">Service クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="7b7be-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7b7be-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7b7be-107">Properties</span></span>  
 <span data-ttu-id="7b7be-108">Service クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7b7be-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="7b7be-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="7b7be-109">BaseAddresses</span></span>  
 <span data-ttu-id="7b7be-110">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="7b7be-110">Data type: string array</span></span>  
  
 <span data-ttu-id="7b7be-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-112">サービスによって使用されるベース アドレスです。</span><span class="sxs-lookup"><span data-stu-id="7b7be-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="7b7be-113">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="7b7be-113">Behaviors</span></span>  
 <span data-ttu-id="7b7be-114">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="7b7be-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="7b7be-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-116">このサービスに関連付けられている動作です。</span><span class="sxs-lookup"><span data-stu-id="7b7be-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="7b7be-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="7b7be-117">ConfigurationName</span></span>  
 <span data-ttu-id="7b7be-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="7b7be-118">Data type: string</span></span>  
  
 <span data-ttu-id="7b7be-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="7b7be-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="7b7be-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="7b7be-121">CounterInstanceName</span></span>  
 <span data-ttu-id="7b7be-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="7b7be-122">Data type: string</span></span>  
  
 <span data-ttu-id="7b7be-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-124">サービスのパフォーマンス カウンターのインスタンスのインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="7b7be-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="7b7be-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="7b7be-125">DistinguishedName</span></span>  
 <span data-ttu-id="7b7be-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="7b7be-126">Data type: string</span></span>  
  
 <span data-ttu-id="7b7be-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-128">アドレスでのサービス名です。</span><span class="sxs-lookup"><span data-stu-id="7b7be-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="7b7be-129">拡張機能</span><span class="sxs-lookup"><span data-stu-id="7b7be-129">Extensions</span></span>  
 <span data-ttu-id="7b7be-130">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="7b7be-130">Data type: string array</span></span>  
  
 <span data-ttu-id="7b7be-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-132">サービス インスタンスの拡張に対するインスタンス コンテキストです。</span><span class="sxs-lookup"><span data-stu-id="7b7be-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="7b7be-133">メタデータ</span><span class="sxs-lookup"><span data-stu-id="7b7be-133">Metadata</span></span>  
 <span data-ttu-id="7b7be-134">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="7b7be-134">Data type: string array</span></span>  
  
 <span data-ttu-id="7b7be-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-136">サービス メタデータの設定です。</span><span class="sxs-lookup"><span data-stu-id="7b7be-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="7b7be-137">name</span><span class="sxs-lookup"><span data-stu-id="7b7be-137">Name</span></span>  
 <span data-ttu-id="7b7be-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="7b7be-138">Data type: string</span></span>  
  
 <span data-ttu-id="7b7be-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-140">このサービスの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="7b7be-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="7b7be-141">名前空間</span><span class="sxs-lookup"><span data-stu-id="7b7be-141">Namespace</span></span>  
 <span data-ttu-id="7b7be-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="7b7be-142">Data type: string</span></span>  
  
 <span data-ttu-id="7b7be-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-144">サービスの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="7b7be-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="7b7be-145">Opened</span><span class="sxs-lookup"><span data-stu-id="7b7be-145">Opened</span></span>  
 <span data-ttu-id="7b7be-146">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="7b7be-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="7b7be-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-148">サービスが開かれた時刻です。</span><span class="sxs-lookup"><span data-stu-id="7b7be-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="7b7be-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="7b7be-149">OutgoingChannels</span></span>  
 <span data-ttu-id="7b7be-150">データ型 : Channel 配列</span><span class="sxs-lookup"><span data-stu-id="7b7be-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="7b7be-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-152">サービス インスタンスから送信しているチャネルです。</span><span class="sxs-lookup"><span data-stu-id="7b7be-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="7b7be-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="7b7be-153">ProcessId</span></span>  
 <span data-ttu-id="7b7be-154">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="7b7be-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="7b7be-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7b7be-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b7be-156">サービスをホストするプロセスのプロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="7b7be-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b7be-157">必要条件</span><span class="sxs-lookup"><span data-stu-id="7b7be-157">Requirements</span></span>  
  
|<span data-ttu-id="7b7be-158">MOF</span><span class="sxs-lookup"><span data-stu-id="7b7be-158">MOF</span></span>|<span data-ttu-id="7b7be-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="7b7be-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7b7be-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="7b7be-160">Namespace</span></span>|<span data-ttu-id="7b7be-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="7b7be-161">Defined in root\ServiceModel</span></span>|
