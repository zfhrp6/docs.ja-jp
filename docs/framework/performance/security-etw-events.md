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
ms.openlocfilehash: a7e28eeabecfe0f1043328618f6e1be143f198a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="8afa3-102">セキュリティ ETW イベント</span><span class="sxs-lookup"><span data-stu-id="8afa3-102">Security ETW Events</span></span>
<span data-ttu-id="8afa3-103"><a name="top"></a> セキュリティ イベントは、厳密な名前の検証時と Authenticode の検証時に発生します。</span><span class="sxs-lookup"><span data-stu-id="8afa3-103"><a name="top"></a> Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="8afa3-104">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="8afa3-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="8afa3-105">StrongNameVerificationStart_V1 イベントと StrongNameVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="8afa3-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="8afa3-106">AuthenticodeVerificationStart_V1 イベントと AuthenticodeVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="8afa3-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="8afa3-107">StrongNameVerificationStart_V1 イベントと StrongNameVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="8afa3-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="8afa3-108">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="8afa3-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="8afa3-109">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8afa3-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="8afa3-110">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="8afa3-110">Keyword for raising the event</span></span>|<span data-ttu-id="8afa3-111">レベル</span><span class="sxs-lookup"><span data-stu-id="8afa3-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8afa3-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="8afa3-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="8afa3-113">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="8afa3-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="8afa3-114">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="8afa3-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="8afa3-115">イベント</span><span class="sxs-lookup"><span data-stu-id="8afa3-115">Event</span></span>|<span data-ttu-id="8afa3-116">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8afa3-116">Event ID</span></span>|<span data-ttu-id="8afa3-117">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="8afa3-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="8afa3-118">181</span><span class="sxs-lookup"><span data-stu-id="8afa3-118">181</span></span>|<span data-ttu-id="8afa3-119">厳密な名前の検証の開始。</span><span class="sxs-lookup"><span data-stu-id="8afa3-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="8afa3-120">182</span><span class="sxs-lookup"><span data-stu-id="8afa3-120">182</span></span>|<span data-ttu-id="8afa3-121">厳密な名前の検証の終了。</span><span class="sxs-lookup"><span data-stu-id="8afa3-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="8afa3-122">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="8afa3-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="8afa3-123">フィールド名</span><span class="sxs-lookup"><span data-stu-id="8afa3-123">Field name</span></span>|<span data-ttu-id="8afa3-124">データ型</span><span class="sxs-lookup"><span data-stu-id="8afa3-124">Data type</span></span>|<span data-ttu-id="8afa3-125">説明</span><span class="sxs-lookup"><span data-stu-id="8afa3-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8afa3-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="8afa3-126">VerificationFlags</span></span>|<span data-ttu-id="8afa3-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8afa3-127">win:UInt32</span></span>|<span data-ttu-id="8afa3-128">検証フラグ。</span><span class="sxs-lookup"><span data-stu-id="8afa3-128">The verification flags.</span></span>|  
|<span data-ttu-id="8afa3-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="8afa3-129">ErrorCode</span></span>|<span data-ttu-id="8afa3-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8afa3-130">win:UInt32</span></span>|<span data-ttu-id="8afa3-131">HResult エラー コード。</span><span class="sxs-lookup"><span data-stu-id="8afa3-131">The HResult error code.</span></span>|  
|<span data-ttu-id="8afa3-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="8afa3-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="8afa3-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8afa3-133">win:UnicodeString</span></span>|<span data-ttu-id="8afa3-134">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="8afa3-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="8afa3-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8afa3-135">ClrInstanceID</span></span>|<span data-ttu-id="8afa3-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8afa3-136">win:UInt16</span></span>|<span data-ttu-id="8afa3-137">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="8afa3-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="8afa3-138">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="8afa3-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="8afa3-139">AuthenticodeVerificationStart_V1 イベントと AuthenticodeVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="8afa3-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="8afa3-140">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="8afa3-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="8afa3-141">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="8afa3-141">Keyword for raising the event</span></span>|<span data-ttu-id="8afa3-142">レベル</span><span class="sxs-lookup"><span data-stu-id="8afa3-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8afa3-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="8afa3-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="8afa3-144">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="8afa3-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="8afa3-145">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="8afa3-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="8afa3-146">イベント</span><span class="sxs-lookup"><span data-stu-id="8afa3-146">Event</span></span>|<span data-ttu-id="8afa3-147">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8afa3-147">Event ID</span></span>|<span data-ttu-id="8afa3-148">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="8afa3-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="8afa3-149">183</span><span class="sxs-lookup"><span data-stu-id="8afa3-149">183</span></span>|<span data-ttu-id="8afa3-150">Authenticode 検証の開始。</span><span class="sxs-lookup"><span data-stu-id="8afa3-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="8afa3-151">184</span><span class="sxs-lookup"><span data-stu-id="8afa3-151">184</span></span>|<span data-ttu-id="8afa3-152">Authenticode 検証の終了。</span><span class="sxs-lookup"><span data-stu-id="8afa3-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="8afa3-153">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="8afa3-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="8afa3-154">フィールド名</span><span class="sxs-lookup"><span data-stu-id="8afa3-154">Field name</span></span>|<span data-ttu-id="8afa3-155">データ型</span><span class="sxs-lookup"><span data-stu-id="8afa3-155">Data type</span></span>|<span data-ttu-id="8afa3-156">説明</span><span class="sxs-lookup"><span data-stu-id="8afa3-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8afa3-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="8afa3-157">VerificationFlags</span></span>|<span data-ttu-id="8afa3-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8afa3-158">win:UInt32</span></span>|<span data-ttu-id="8afa3-159">検証フラグ。</span><span class="sxs-lookup"><span data-stu-id="8afa3-159">The verification flags.</span></span>|  
|<span data-ttu-id="8afa3-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="8afa3-160">ErrorCode</span></span>|<span data-ttu-id="8afa3-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="8afa3-161">win:UInt32</span></span>|<span data-ttu-id="8afa3-162">HResult エラー コード。</span><span class="sxs-lookup"><span data-stu-id="8afa3-162">The HResult error code.</span></span>|  
|<span data-ttu-id="8afa3-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="8afa3-163">ModulePath</span></span>|<span data-ttu-id="8afa3-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8afa3-164">win:UnicodeString</span></span>|<span data-ttu-id="8afa3-165">モジュール パス</span><span class="sxs-lookup"><span data-stu-id="8afa3-165">The module path.</span></span>|  
|<span data-ttu-id="8afa3-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8afa3-166">ClrInstanceID</span></span>|<span data-ttu-id="8afa3-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8afa3-167">win:UInt16</span></span>|<span data-ttu-id="8afa3-168">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="8afa3-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8afa3-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="8afa3-169">See Also</span></span>  
 [<span data-ttu-id="8afa3-170">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="8afa3-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
