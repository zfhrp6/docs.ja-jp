---
title: "セキュリティ ETW イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abf6e6896267b6d1c8449b020230381923f38f1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="5252f-102">セキュリティ ETW イベント</span><span class="sxs-lookup"><span data-stu-id="5252f-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="5252f-103">セキュリティ イベントは、厳密な名前の検証時と Authenticode の検証時に発生します。</span><span class="sxs-lookup"><span data-stu-id="5252f-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="5252f-104">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="5252f-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="5252f-105">StrongNameVerificationStart_V1 イベントと StrongNameVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="5252f-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="5252f-106">AuthenticodeVerificationStart_V1 イベントと AuthenticodeVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="5252f-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="5252f-107">StrongNameVerificationStart_V1 イベントと StrongNameVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="5252f-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="5252f-108">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="5252f-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="5252f-109">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5252f-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5252f-110">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="5252f-110">Keyword for raising the event</span></span>|<span data-ttu-id="5252f-111">レベル</span><span class="sxs-lookup"><span data-stu-id="5252f-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5252f-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="5252f-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="5252f-113">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="5252f-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="5252f-114">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="5252f-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5252f-115">イベント</span><span class="sxs-lookup"><span data-stu-id="5252f-115">Event</span></span>|<span data-ttu-id="5252f-116">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5252f-116">Event ID</span></span>|<span data-ttu-id="5252f-117">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="5252f-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="5252f-118">181</span><span class="sxs-lookup"><span data-stu-id="5252f-118">181</span></span>|<span data-ttu-id="5252f-119">厳密な名前の検証の開始。</span><span class="sxs-lookup"><span data-stu-id="5252f-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="5252f-120">182</span><span class="sxs-lookup"><span data-stu-id="5252f-120">182</span></span>|<span data-ttu-id="5252f-121">厳密な名前の検証の終了。</span><span class="sxs-lookup"><span data-stu-id="5252f-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="5252f-122">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="5252f-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5252f-123">フィールド名</span><span class="sxs-lookup"><span data-stu-id="5252f-123">Field name</span></span>|<span data-ttu-id="5252f-124">データ型</span><span class="sxs-lookup"><span data-stu-id="5252f-124">Data type</span></span>|<span data-ttu-id="5252f-125">説明</span><span class="sxs-lookup"><span data-stu-id="5252f-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5252f-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="5252f-126">VerificationFlags</span></span>|<span data-ttu-id="5252f-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5252f-127">win:UInt32</span></span>|<span data-ttu-id="5252f-128">検証フラグ。</span><span class="sxs-lookup"><span data-stu-id="5252f-128">The verification flags.</span></span>|  
|<span data-ttu-id="5252f-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="5252f-129">ErrorCode</span></span>|<span data-ttu-id="5252f-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5252f-130">win:UInt32</span></span>|<span data-ttu-id="5252f-131">HResult エラー コード。</span><span class="sxs-lookup"><span data-stu-id="5252f-131">The HResult error code.</span></span>|  
|<span data-ttu-id="5252f-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="5252f-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="5252f-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5252f-133">win:UnicodeString</span></span>|<span data-ttu-id="5252f-134">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="5252f-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="5252f-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5252f-135">ClrInstanceID</span></span>|<span data-ttu-id="5252f-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5252f-136">win:UInt16</span></span>|<span data-ttu-id="5252f-137">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="5252f-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="5252f-138">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="5252f-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="5252f-139">AuthenticodeVerificationStart_V1 イベントと AuthenticodeVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="5252f-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="5252f-140">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="5252f-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="5252f-141">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="5252f-141">Keyword for raising the event</span></span>|<span data-ttu-id="5252f-142">レベル</span><span class="sxs-lookup"><span data-stu-id="5252f-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5252f-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="5252f-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="5252f-144">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="5252f-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="5252f-145">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="5252f-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5252f-146">イベント</span><span class="sxs-lookup"><span data-stu-id="5252f-146">Event</span></span>|<span data-ttu-id="5252f-147">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5252f-147">Event ID</span></span>|<span data-ttu-id="5252f-148">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="5252f-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="5252f-149">183</span><span class="sxs-lookup"><span data-stu-id="5252f-149">183</span></span>|<span data-ttu-id="5252f-150">Authenticode 検証の開始。</span><span class="sxs-lookup"><span data-stu-id="5252f-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="5252f-151">184</span><span class="sxs-lookup"><span data-stu-id="5252f-151">184</span></span>|<span data-ttu-id="5252f-152">Authenticode 検証の終了。</span><span class="sxs-lookup"><span data-stu-id="5252f-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="5252f-153">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="5252f-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5252f-154">フィールド名</span><span class="sxs-lookup"><span data-stu-id="5252f-154">Field name</span></span>|<span data-ttu-id="5252f-155">データ型</span><span class="sxs-lookup"><span data-stu-id="5252f-155">Data type</span></span>|<span data-ttu-id="5252f-156">説明</span><span class="sxs-lookup"><span data-stu-id="5252f-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5252f-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="5252f-157">VerificationFlags</span></span>|<span data-ttu-id="5252f-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5252f-158">win:UInt32</span></span>|<span data-ttu-id="5252f-159">検証フラグ。</span><span class="sxs-lookup"><span data-stu-id="5252f-159">The verification flags.</span></span>|  
|<span data-ttu-id="5252f-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="5252f-160">ErrorCode</span></span>|<span data-ttu-id="5252f-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5252f-161">win:UInt32</span></span>|<span data-ttu-id="5252f-162">HResult エラー コード。</span><span class="sxs-lookup"><span data-stu-id="5252f-162">The HResult error code.</span></span>|  
|<span data-ttu-id="5252f-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="5252f-163">ModulePath</span></span>|<span data-ttu-id="5252f-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5252f-164">win:UnicodeString</span></span>|<span data-ttu-id="5252f-165">モジュール パス</span><span class="sxs-lookup"><span data-stu-id="5252f-165">The module path.</span></span>|  
|<span data-ttu-id="5252f-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5252f-166">ClrInstanceID</span></span>|<span data-ttu-id="5252f-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5252f-167">win:UInt16</span></span>|<span data-ttu-id="5252f-168">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="5252f-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5252f-169">参照</span><span class="sxs-lookup"><span data-stu-id="5252f-169">See Also</span></span>  
 [<span data-ttu-id="5252f-170">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="5252f-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
