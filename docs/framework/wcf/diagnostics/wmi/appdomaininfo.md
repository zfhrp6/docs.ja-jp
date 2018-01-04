---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed5053dd69628a9f5ff7318ce7fe772f42de6e24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="57765-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="57765-102">AppDomainInfo</span></span>
<span data-ttu-id="57765-103">アプリケーション ドメイン情報</span><span class="sxs-lookup"><span data-stu-id="57765-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57765-104">構文</span><span class="sxs-lookup"><span data-stu-id="57765-104">Syntax</span></span>  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="57765-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="57765-105">Methods</span></span>  
 <span data-ttu-id="57765-106">AppDomainInfo クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="57765-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="57765-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="57765-107">Properties</span></span>  
 <span data-ttu-id="57765-108">AppDomainInfo クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="57765-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="57765-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="57765-109">AppDomainId</span></span>  
 <span data-ttu-id="57765-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="57765-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="57765-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="57765-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57765-112">AppDomain の ID です。</span><span class="sxs-lookup"><span data-stu-id="57765-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="57765-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="57765-113">IsDefault</span></span>  
 <span data-ttu-id="57765-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="57765-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="57765-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="57765-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57765-116">AppDomain が既定の AppDomain かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="57765-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="57765-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="57765-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="57765-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="57765-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="57765-119">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="57765-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="57765-120">非整形式メッセージをログに記録するかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="57765-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="57765-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="57765-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="57765-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="57765-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="57765-123">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="57765-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="57765-124">メッセージをサービス レベルでトレースするかどうかを指定する値です (暗号化およびトランスポート関連の変換前)。</span><span class="sxs-lookup"><span data-stu-id="57765-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="57765-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="57765-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="57765-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="57765-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="57765-127">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="57765-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="57765-128">メッセージをトランスポート レベルでトレースするかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="57765-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="57765-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="57765-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="57765-130">データ型 : TraceListener 配列</span><span class="sxs-lookup"><span data-stu-id="57765-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="57765-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="57765-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57765-132">System.Wmi.MessageLogging トレース ソースをリッスンするコレクション トレース リスナーです。</span><span class="sxs-lookup"><span data-stu-id="57765-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="57765-133">name</span><span class="sxs-lookup"><span data-stu-id="57765-133">Name</span></span>  
 <span data-ttu-id="57765-134">データ型: string</span><span class="sxs-lookup"><span data-stu-id="57765-134">Data type: string</span></span>  
  
 <span data-ttu-id="57765-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="57765-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57765-136">AppDomain の名前です。</span><span class="sxs-lookup"><span data-stu-id="57765-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="57765-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="57765-137">PerformanceCounters</span></span>  
 <span data-ttu-id="57765-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="57765-138">Data type: string</span></span>  
  
 <span data-ttu-id="57765-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="57765-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57765-140">AppDomain におけるアクティブなパフォーマンス カウンターのスコープです。</span><span class="sxs-lookup"><span data-stu-id="57765-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="57765-141">ProcessId</span><span class="sxs-lookup"><span data-stu-id="57765-141">ProcessId</span></span>  
 <span data-ttu-id="57765-142">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="57765-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="57765-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="57765-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57765-144">プロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="57765-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="57765-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="57765-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="57765-146">データ型: string</span><span class="sxs-lookup"><span data-stu-id="57765-146">Data type: string</span></span>  
  
 <span data-ttu-id="57765-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="57765-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57765-148">サービスの構成へのパスです。</span><span class="sxs-lookup"><span data-stu-id="57765-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="57765-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="57765-149">TraceLevel</span></span>  
 <span data-ttu-id="57765-150">データ型: string</span><span class="sxs-lookup"><span data-stu-id="57765-150">Data type: string</span></span>  
  
 <span data-ttu-id="57765-151">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="57765-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="57765-152">System.Wmi トレース ソースのトレース レベル。</span><span class="sxs-lookup"><span data-stu-id="57765-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="57765-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="57765-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="57765-154">データ型 : TraceListener 配列</span><span class="sxs-lookup"><span data-stu-id="57765-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="57765-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="57765-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57765-156">System.ServiceModel トレース ソースのリスナーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="57765-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57765-157">必要条件</span><span class="sxs-lookup"><span data-stu-id="57765-157">Requirements</span></span>  
  
|<span data-ttu-id="57765-158">MOF</span><span class="sxs-lookup"><span data-stu-id="57765-158">MOF</span></span>|<span data-ttu-id="57765-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="57765-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="57765-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="57765-160">Namespace</span></span>|<span data-ttu-id="57765-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="57765-161">Defined in root\ServiceModel</span></span>|
