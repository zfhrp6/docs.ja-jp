---
title: MsmqBindingElementBase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10e476931ef07ec694dff200e64ce2ded74c8dfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="e525e-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="e525e-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="e525e-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="e525e-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e525e-104">構文</span><span class="sxs-lookup"><span data-stu-id="e525e-104">Syntax</span></span>  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e525e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e525e-105">Methods</span></span>  
 <span data-ttu-id="e525e-106">MsmqBindingElementBase クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="e525e-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e525e-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e525e-107">Properties</span></span>  
 <span data-ttu-id="e525e-108">MsmqBindingElementBase クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="e525e-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="e525e-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="e525e-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="e525e-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="e525e-110">Data type: string</span></span>  
  
 <span data-ttu-id="e525e-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-112">アプリケーションごとの配信不能キューの場所が含まれている URI です。ここには、期限切れのメッセージや、転送または配信に失敗したメッセージが配置されます。</span><span class="sxs-lookup"><span data-stu-id="e525e-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="e525e-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="e525e-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="e525e-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="e525e-114">Data type: string</span></span>  
  
 <span data-ttu-id="e525e-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-116">使用する配信不能キューの型を示す列挙型の値です。</span><span class="sxs-lookup"><span data-stu-id="e525e-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="e525e-117">Durable</span><span class="sxs-lookup"><span data-stu-id="e525e-117">Durable</span></span>  
 <span data-ttu-id="e525e-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e525e-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e525e-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-120">このバインディングによって処理されるメッセージが永続的なものか不安定なものかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="e525e-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="e525e-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="e525e-121">ExactlyOnce</span></span>  
 <span data-ttu-id="e525e-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e525e-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="e525e-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-124">このバインディングで処理されるメッセージが正確に 1 回だけ受信されるかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="e525e-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="e525e-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="e525e-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="e525e-126">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="e525e-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="e525e-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-128">受信アプリケーションにメッセージを配信する再試行サイクルの最大数です。</span><span class="sxs-lookup"><span data-stu-id="e525e-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="e525e-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="e525e-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="e525e-130">データ型: string</span><span class="sxs-lookup"><span data-stu-id="e525e-130">Data type: string</span></span>  
  
 <span data-ttu-id="e525e-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-132">有害メッセージの処理の設定です。</span><span class="sxs-lookup"><span data-stu-id="e525e-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="e525e-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="e525e-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="e525e-134">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="e525e-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="e525e-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-136">アプリケーション キューから読み取られるメッセージの即時再試行の最大回数です。</span><span class="sxs-lookup"><span data-stu-id="e525e-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="e525e-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="e525e-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="e525e-138">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="e525e-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="e525e-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-140">すぐに配信できなかったメッセージを配信しようとするときの、再試行サイクルの時間遅延を示す値です。</span><span class="sxs-lookup"><span data-stu-id="e525e-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="e525e-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="e525e-141">TimeToLive</span></span>  
 <span data-ttu-id="e525e-142">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="e525e-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="e525e-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-144">このバインディングで処理されるメッセージの期限が切れるまで、メッセージをキュー内で保持する時間です。</span><span class="sxs-lookup"><span data-stu-id="e525e-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="e525e-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="e525e-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="e525e-146">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e525e-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="e525e-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-148">このバインディングにより処理されるメッセージをトレースするかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="e525e-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="e525e-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="e525e-149">UseSourceJournal</span></span>  
 <span data-ttu-id="e525e-150">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e525e-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="e525e-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e525e-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e525e-152">このバインディングにより処理されるメッセージのコピーをソース ジャーナル キューに保存するかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="e525e-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e525e-153">必要条件</span><span class="sxs-lookup"><span data-stu-id="e525e-153">Requirements</span></span>  
  
|<span data-ttu-id="e525e-154">MOF</span><span class="sxs-lookup"><span data-stu-id="e525e-154">MOF</span></span>|<span data-ttu-id="e525e-155">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="e525e-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e525e-156">Namespace</span><span class="sxs-lookup"><span data-stu-id="e525e-156">Namespace</span></span>|<span data-ttu-id="e525e-157">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="e525e-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e525e-158">参照</span><span class="sxs-lookup"><span data-stu-id="e525e-158">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
