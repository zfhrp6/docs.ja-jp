---
title: セキュリティ ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e02274b63ddf7df42d26621791de0286df9655b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395513"
---
# <a name="security-etw-events"></a><span data-ttu-id="5b712-102">セキュリティ ETW イベント</span><span class="sxs-lookup"><span data-stu-id="5b712-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="5b712-103">セキュリティ イベントは、厳密な名前の検証時と Authenticode の検証時に発生します。</span><span class="sxs-lookup"><span data-stu-id="5b712-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="5b712-104">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="5b712-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="5b712-105">StrongNameVerificationStart_V1 イベントと StrongNameVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="5b712-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="5b712-106">AuthenticodeVerificationStart_V1 イベントと AuthenticodeVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="5b712-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="5b712-107">StrongNameVerificationStart_V1 イベントと StrongNameVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="5b712-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="5b712-108">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="5b712-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="5b712-109">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5b712-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5b712-110">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="5b712-110">Keyword for raising the event</span></span>|<span data-ttu-id="5b712-111">レベル</span><span class="sxs-lookup"><span data-stu-id="5b712-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5b712-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="5b712-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="5b712-113">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="5b712-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="5b712-114">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="5b712-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5b712-115">イベント</span><span class="sxs-lookup"><span data-stu-id="5b712-115">Event</span></span>|<span data-ttu-id="5b712-116">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5b712-116">Event ID</span></span>|<span data-ttu-id="5b712-117">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="5b712-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="5b712-118">181</span><span class="sxs-lookup"><span data-stu-id="5b712-118">181</span></span>|<span data-ttu-id="5b712-119">厳密な名前の検証の開始。</span><span class="sxs-lookup"><span data-stu-id="5b712-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="5b712-120">182</span><span class="sxs-lookup"><span data-stu-id="5b712-120">182</span></span>|<span data-ttu-id="5b712-121">厳密な名前の検証の終了。</span><span class="sxs-lookup"><span data-stu-id="5b712-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="5b712-122">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="5b712-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5b712-123">フィールド名</span><span class="sxs-lookup"><span data-stu-id="5b712-123">Field name</span></span>|<span data-ttu-id="5b712-124">データ型</span><span class="sxs-lookup"><span data-stu-id="5b712-124">Data type</span></span>|<span data-ttu-id="5b712-125">説明</span><span class="sxs-lookup"><span data-stu-id="5b712-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5b712-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="5b712-126">VerificationFlags</span></span>|<span data-ttu-id="5b712-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5b712-127">win:UInt32</span></span>|<span data-ttu-id="5b712-128">検証フラグ。</span><span class="sxs-lookup"><span data-stu-id="5b712-128">The verification flags.</span></span>|  
|<span data-ttu-id="5b712-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="5b712-129">ErrorCode</span></span>|<span data-ttu-id="5b712-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5b712-130">win:UInt32</span></span>|<span data-ttu-id="5b712-131">HResult エラー コード。</span><span class="sxs-lookup"><span data-stu-id="5b712-131">The HResult error code.</span></span>|  
|<span data-ttu-id="5b712-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="5b712-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="5b712-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5b712-133">win:UnicodeString</span></span>|<span data-ttu-id="5b712-134">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="5b712-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="5b712-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5b712-135">ClrInstanceID</span></span>|<span data-ttu-id="5b712-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5b712-136">win:UInt16</span></span>|<span data-ttu-id="5b712-137">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="5b712-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="5b712-138">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="5b712-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="5b712-139">AuthenticodeVerificationStart_V1 イベントと AuthenticodeVerificationStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="5b712-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="5b712-140">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="5b712-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="5b712-141">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="5b712-141">Keyword for raising the event</span></span>|<span data-ttu-id="5b712-142">レベル</span><span class="sxs-lookup"><span data-stu-id="5b712-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5b712-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="5b712-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="5b712-144">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="5b712-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="5b712-145">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="5b712-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5b712-146">イベント</span><span class="sxs-lookup"><span data-stu-id="5b712-146">Event</span></span>|<span data-ttu-id="5b712-147">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5b712-147">Event ID</span></span>|<span data-ttu-id="5b712-148">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="5b712-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="5b712-149">183</span><span class="sxs-lookup"><span data-stu-id="5b712-149">183</span></span>|<span data-ttu-id="5b712-150">Authenticode 検証の開始。</span><span class="sxs-lookup"><span data-stu-id="5b712-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="5b712-151">184</span><span class="sxs-lookup"><span data-stu-id="5b712-151">184</span></span>|<span data-ttu-id="5b712-152">Authenticode 検証の終了。</span><span class="sxs-lookup"><span data-stu-id="5b712-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="5b712-153">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="5b712-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5b712-154">フィールド名</span><span class="sxs-lookup"><span data-stu-id="5b712-154">Field name</span></span>|<span data-ttu-id="5b712-155">データ型</span><span class="sxs-lookup"><span data-stu-id="5b712-155">Data type</span></span>|<span data-ttu-id="5b712-156">説明</span><span class="sxs-lookup"><span data-stu-id="5b712-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5b712-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="5b712-157">VerificationFlags</span></span>|<span data-ttu-id="5b712-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5b712-158">win:UInt32</span></span>|<span data-ttu-id="5b712-159">検証フラグ。</span><span class="sxs-lookup"><span data-stu-id="5b712-159">The verification flags.</span></span>|  
|<span data-ttu-id="5b712-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="5b712-160">ErrorCode</span></span>|<span data-ttu-id="5b712-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5b712-161">win:UInt32</span></span>|<span data-ttu-id="5b712-162">HResult エラー コード。</span><span class="sxs-lookup"><span data-stu-id="5b712-162">The HResult error code.</span></span>|  
|<span data-ttu-id="5b712-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="5b712-163">ModulePath</span></span>|<span data-ttu-id="5b712-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5b712-164">win:UnicodeString</span></span>|<span data-ttu-id="5b712-165">モジュール パス</span><span class="sxs-lookup"><span data-stu-id="5b712-165">The module path.</span></span>|  
|<span data-ttu-id="5b712-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5b712-166">ClrInstanceID</span></span>|<span data-ttu-id="5b712-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5b712-167">win:UInt16</span></span>|<span data-ttu-id="5b712-168">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="5b712-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b712-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b712-169">See Also</span></span>  
 [<span data-ttu-id="5b712-170">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="5b712-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
