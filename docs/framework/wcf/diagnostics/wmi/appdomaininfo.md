---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 7189448a930298837089cf3ac2743cb7e073ae02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486982"
---
# <a name="appdomaininfo"></a><span data-ttu-id="a3920-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="a3920-102">AppDomainInfo</span></span>
<span data-ttu-id="a3920-103">アプリケーション ドメイン情報</span><span class="sxs-lookup"><span data-stu-id="a3920-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3920-104">構文</span><span class="sxs-lookup"><span data-stu-id="a3920-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a3920-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a3920-105">Methods</span></span>  
 <span data-ttu-id="a3920-106">AppDomainInfo クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="a3920-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a3920-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a3920-107">Properties</span></span>  
 <span data-ttu-id="a3920-108">AppDomainInfo クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="a3920-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="a3920-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="a3920-109">AppDomainId</span></span>  
 <span data-ttu-id="a3920-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="a3920-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="a3920-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3920-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3920-112">AppDomain の ID です。</span><span class="sxs-lookup"><span data-stu-id="a3920-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="a3920-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="a3920-113">IsDefault</span></span>  
 <span data-ttu-id="a3920-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="a3920-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a3920-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3920-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3920-116">AppDomain が既定の AppDomain かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a3920-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="a3920-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="a3920-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="a3920-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="a3920-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="a3920-119">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="a3920-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="a3920-120">非整形式メッセージをログに記録するかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="a3920-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="a3920-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="a3920-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="a3920-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="a3920-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a3920-123">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="a3920-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="a3920-124">メッセージをサービス レベルでトレースするかどうかを指定する値です (暗号化およびトランスポート関連の変換前)。</span><span class="sxs-lookup"><span data-stu-id="a3920-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="a3920-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="a3920-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="a3920-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="a3920-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="a3920-127">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="a3920-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="a3920-128">メッセージをトランスポート レベルでトレースするかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="a3920-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="a3920-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="a3920-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="a3920-130">データ型 : TraceListener 配列</span><span class="sxs-lookup"><span data-stu-id="a3920-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="a3920-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3920-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3920-132">System.Wmi.MessageLogging トレース ソースをリッスンするコレクション トレース リスナーです。</span><span class="sxs-lookup"><span data-stu-id="a3920-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="a3920-133">名前</span><span class="sxs-lookup"><span data-stu-id="a3920-133">Name</span></span>  
 <span data-ttu-id="a3920-134">データ型: string</span><span class="sxs-lookup"><span data-stu-id="a3920-134">Data type: string</span></span>  
  
 <span data-ttu-id="a3920-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3920-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3920-136">AppDomain の名前です。</span><span class="sxs-lookup"><span data-stu-id="a3920-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="a3920-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="a3920-137">PerformanceCounters</span></span>  
 <span data-ttu-id="a3920-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="a3920-138">Data type: string</span></span>  
  
 <span data-ttu-id="a3920-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3920-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3920-140">AppDomain におけるアクティブなパフォーマンス カウンターのスコープです。</span><span class="sxs-lookup"><span data-stu-id="a3920-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="a3920-141">ProcessId</span><span class="sxs-lookup"><span data-stu-id="a3920-141">ProcessId</span></span>  
 <span data-ttu-id="a3920-142">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="a3920-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="a3920-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3920-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3920-144">プロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="a3920-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="a3920-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="a3920-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="a3920-146">データ型: string</span><span class="sxs-lookup"><span data-stu-id="a3920-146">Data type: string</span></span>  
  
 <span data-ttu-id="a3920-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3920-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3920-148">サービスの構成へのパスです。</span><span class="sxs-lookup"><span data-stu-id="a3920-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="a3920-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="a3920-149">TraceLevel</span></span>  
 <span data-ttu-id="a3920-150">データ型: string</span><span class="sxs-lookup"><span data-stu-id="a3920-150">Data type: string</span></span>  
  
 <span data-ttu-id="a3920-151">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="a3920-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="a3920-152">System.Wmi トレース ソースのトレース レベル。</span><span class="sxs-lookup"><span data-stu-id="a3920-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="a3920-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="a3920-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="a3920-154">データ型 : TraceListener 配列</span><span class="sxs-lookup"><span data-stu-id="a3920-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="a3920-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a3920-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3920-156">System.ServiceModel トレース ソースのリスナーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="a3920-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3920-157">要件</span><span class="sxs-lookup"><span data-stu-id="a3920-157">Requirements</span></span>  
  
|<span data-ttu-id="a3920-158">MOF</span><span class="sxs-lookup"><span data-stu-id="a3920-158">MOF</span></span>|<span data-ttu-id="a3920-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="a3920-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a3920-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="a3920-160">Namespace</span></span>|<span data-ttu-id="a3920-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="a3920-161">Defined in root\ServiceModel</span></span>|
