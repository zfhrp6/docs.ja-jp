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
ms.openlocfilehash: 027366e7bf7abd285ef65da2040514b4b9908213
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="service"></a><span data-ttu-id="32982-102">サービス</span><span class="sxs-lookup"><span data-stu-id="32982-102">Service</span></span>
<span data-ttu-id="32982-103">サービス</span><span class="sxs-lookup"><span data-stu-id="32982-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32982-104">構文</span><span class="sxs-lookup"><span data-stu-id="32982-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="32982-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="32982-105">Methods</span></span>  
 <span data-ttu-id="32982-106">Service クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="32982-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="32982-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="32982-107">Properties</span></span>  
 <span data-ttu-id="32982-108">Service クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="32982-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="32982-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="32982-109">BaseAddresses</span></span>  
 <span data-ttu-id="32982-110">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="32982-110">Data type: string array</span></span>  
  
 <span data-ttu-id="32982-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-112">サービスによって使用されるベース アドレスです。</span><span class="sxs-lookup"><span data-stu-id="32982-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="32982-113">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="32982-113">Behaviors</span></span>  
 <span data-ttu-id="32982-114">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="32982-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="32982-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-116">このサービスに関連付けられている動作です。</span><span class="sxs-lookup"><span data-stu-id="32982-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="32982-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="32982-117">ConfigurationName</span></span>  
 <span data-ttu-id="32982-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="32982-118">Data type: string</span></span>  
  
 <span data-ttu-id="32982-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="32982-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="32982-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="32982-121">CounterInstanceName</span></span>  
 <span data-ttu-id="32982-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="32982-122">Data type: string</span></span>  
  
 <span data-ttu-id="32982-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-124">サービスのパフォーマンス カウンターのインスタンスのインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="32982-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="32982-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="32982-125">DistinguishedName</span></span>  
 <span data-ttu-id="32982-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="32982-126">Data type: string</span></span>  
  
 <span data-ttu-id="32982-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-128">アドレスでのサービス名です。</span><span class="sxs-lookup"><span data-stu-id="32982-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="32982-129">拡張機能</span><span class="sxs-lookup"><span data-stu-id="32982-129">Extensions</span></span>  
 <span data-ttu-id="32982-130">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="32982-130">Data type: string array</span></span>  
  
 <span data-ttu-id="32982-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-132">サービス インスタンスの拡張に対するインスタンス コンテキストです。</span><span class="sxs-lookup"><span data-stu-id="32982-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="32982-133">メタデータ</span><span class="sxs-lookup"><span data-stu-id="32982-133">Metadata</span></span>  
 <span data-ttu-id="32982-134">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="32982-134">Data type: string array</span></span>  
  
 <span data-ttu-id="32982-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-136">サービス メタデータの設定です。</span><span class="sxs-lookup"><span data-stu-id="32982-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="32982-137">名前</span><span class="sxs-lookup"><span data-stu-id="32982-137">Name</span></span>  
 <span data-ttu-id="32982-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="32982-138">Data type: string</span></span>  
  
 <span data-ttu-id="32982-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-140">このサービスの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="32982-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="32982-141">名前空間</span><span class="sxs-lookup"><span data-stu-id="32982-141">Namespace</span></span>  
 <span data-ttu-id="32982-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="32982-142">Data type: string</span></span>  
  
 <span data-ttu-id="32982-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-144">サービスの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="32982-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="32982-145">Opened</span><span class="sxs-lookup"><span data-stu-id="32982-145">Opened</span></span>  
 <span data-ttu-id="32982-146">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="32982-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="32982-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-148">サービスが開かれた時刻です。</span><span class="sxs-lookup"><span data-stu-id="32982-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="32982-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="32982-149">OutgoingChannels</span></span>  
 <span data-ttu-id="32982-150">データ型 : Channel 配列</span><span class="sxs-lookup"><span data-stu-id="32982-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="32982-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-152">サービス インスタンスから送信しているチャネルです。</span><span class="sxs-lookup"><span data-stu-id="32982-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="32982-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="32982-153">ProcessId</span></span>  
 <span data-ttu-id="32982-154">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="32982-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="32982-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="32982-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32982-156">サービスをホストするプロセスのプロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="32982-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32982-157">要件</span><span class="sxs-lookup"><span data-stu-id="32982-157">Requirements</span></span>  
  
|<span data-ttu-id="32982-158">MOF</span><span class="sxs-lookup"><span data-stu-id="32982-158">MOF</span></span>|<span data-ttu-id="32982-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="32982-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="32982-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="32982-160">Namespace</span></span>|<span data-ttu-id="32982-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="32982-161">Defined in root\ServiceModel</span></span>|
