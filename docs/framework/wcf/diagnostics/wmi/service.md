---
title: サービス
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: 0cfeb178e26f6c93e29210accf5d7866cc1fca02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487148"
---
# <a name="service"></a><span data-ttu-id="978d8-102">サービス</span><span class="sxs-lookup"><span data-stu-id="978d8-102">Service</span></span>
<span data-ttu-id="978d8-103">サービス</span><span class="sxs-lookup"><span data-stu-id="978d8-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="978d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="978d8-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="978d8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="978d8-105">Methods</span></span>  
 <span data-ttu-id="978d8-106">Service クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="978d8-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="978d8-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="978d8-107">Properties</span></span>  
 <span data-ttu-id="978d8-108">Service クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="978d8-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="978d8-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="978d8-109">BaseAddresses</span></span>  
 <span data-ttu-id="978d8-110">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="978d8-110">Data type: string array</span></span>  
  
 <span data-ttu-id="978d8-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-112">サービスによって使用されるベース アドレスです。</span><span class="sxs-lookup"><span data-stu-id="978d8-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="978d8-113">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="978d8-113">Behaviors</span></span>  
 <span data-ttu-id="978d8-114">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="978d8-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="978d8-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-116">このサービスに関連付けられている動作です。</span><span class="sxs-lookup"><span data-stu-id="978d8-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="978d8-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="978d8-117">ConfigurationName</span></span>  
 <span data-ttu-id="978d8-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="978d8-118">Data type: string</span></span>  
  
 <span data-ttu-id="978d8-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="978d8-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="978d8-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="978d8-121">CounterInstanceName</span></span>  
 <span data-ttu-id="978d8-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="978d8-122">Data type: string</span></span>  
  
 <span data-ttu-id="978d8-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-124">サービスのパフォーマンス カウンターのインスタンスのインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="978d8-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="978d8-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="978d8-125">DistinguishedName</span></span>  
 <span data-ttu-id="978d8-126">データ型: string</span><span class="sxs-lookup"><span data-stu-id="978d8-126">Data type: string</span></span>  
  
 <span data-ttu-id="978d8-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-128">アドレスでのサービス名です。</span><span class="sxs-lookup"><span data-stu-id="978d8-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="978d8-129">拡張機能</span><span class="sxs-lookup"><span data-stu-id="978d8-129">Extensions</span></span>  
 <span data-ttu-id="978d8-130">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="978d8-130">Data type: string array</span></span>  
  
 <span data-ttu-id="978d8-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-132">サービス インスタンスの拡張に対するインスタンス コンテキストです。</span><span class="sxs-lookup"><span data-stu-id="978d8-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="978d8-133">メタデータ</span><span class="sxs-lookup"><span data-stu-id="978d8-133">Metadata</span></span>  
 <span data-ttu-id="978d8-134">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="978d8-134">Data type: string array</span></span>  
  
 <span data-ttu-id="978d8-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-136">サービス メタデータの設定です。</span><span class="sxs-lookup"><span data-stu-id="978d8-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="978d8-137">名前</span><span class="sxs-lookup"><span data-stu-id="978d8-137">Name</span></span>  
 <span data-ttu-id="978d8-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="978d8-138">Data type: string</span></span>  
  
 <span data-ttu-id="978d8-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-140">このサービスの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="978d8-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="978d8-141">名前空間</span><span class="sxs-lookup"><span data-stu-id="978d8-141">Namespace</span></span>  
 <span data-ttu-id="978d8-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="978d8-142">Data type: string</span></span>  
  
 <span data-ttu-id="978d8-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-144">サービスの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="978d8-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="978d8-145">Opened</span><span class="sxs-lookup"><span data-stu-id="978d8-145">Opened</span></span>  
 <span data-ttu-id="978d8-146">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="978d8-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="978d8-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-148">サービスが開かれた時刻です。</span><span class="sxs-lookup"><span data-stu-id="978d8-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="978d8-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="978d8-149">OutgoingChannels</span></span>  
 <span data-ttu-id="978d8-150">データ型 : Channel 配列</span><span class="sxs-lookup"><span data-stu-id="978d8-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="978d8-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-152">サービス インスタンスから送信しているチャネルです。</span><span class="sxs-lookup"><span data-stu-id="978d8-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="978d8-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="978d8-153">ProcessId</span></span>  
 <span data-ttu-id="978d8-154">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="978d8-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="978d8-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="978d8-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="978d8-156">サービスをホストするプロセスのプロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="978d8-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="978d8-157">要件</span><span class="sxs-lookup"><span data-stu-id="978d8-157">Requirements</span></span>  
  
|<span data-ttu-id="978d8-158">MOF</span><span class="sxs-lookup"><span data-stu-id="978d8-158">MOF</span></span>|<span data-ttu-id="978d8-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="978d8-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="978d8-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="978d8-160">Namespace</span></span>|<span data-ttu-id="978d8-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="978d8-161">Defined in root\ServiceModel</span></span>|
