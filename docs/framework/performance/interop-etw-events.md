---
title: "相互運用 ETW イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55097e38161ea5c76f4e46584241344ec5a52cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="0810a-102">相互運用 ETW イベント</span><span class="sxs-lookup"><span data-stu-id="0810a-102">Interop ETW Events</span></span>
<span data-ttu-id="0810a-103"><a name="top"></a> 相互運用イベントは、Microsoft intermediate language (MSIL) のスタブ生成とキャッシュに関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="0810a-103"><a name="top"></a> Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="0810a-104">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="0810a-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="0810a-105">ILStubGenerated イベント</span><span class="sxs-lookup"><span data-stu-id="0810a-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="0810a-106">ILStubCacheHit イベント</span><span class="sxs-lookup"><span data-stu-id="0810a-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="0810a-107">ILStubGenerated イベント</span><span class="sxs-lookup"><span data-stu-id="0810a-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="0810a-108">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="0810a-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="0810a-109">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0810a-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0810a-110">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="0810a-110">Keyword for raising the event</span></span>|<span data-ttu-id="0810a-111">レベル</span><span class="sxs-lookup"><span data-stu-id="0810a-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0810a-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="0810a-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="0810a-113">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="0810a-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="0810a-114">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="0810a-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0810a-115">イベント</span><span class="sxs-lookup"><span data-stu-id="0810a-115">Event</span></span>|<span data-ttu-id="0810a-116">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0810a-116">Event ID</span></span>|<span data-ttu-id="0810a-117">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="0810a-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="0810a-118">88</span><span class="sxs-lookup"><span data-stu-id="0810a-118">88</span></span>|<span data-ttu-id="0810a-119">MSIL スタブが生成された。</span><span class="sxs-lookup"><span data-stu-id="0810a-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="0810a-120">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="0810a-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0810a-121">フィールド名</span><span class="sxs-lookup"><span data-stu-id="0810a-121">Field name</span></span>|<span data-ttu-id="0810a-122">データ型</span><span class="sxs-lookup"><span data-stu-id="0810a-122">Data type</span></span>|<span data-ttu-id="0810a-123">説明</span><span class="sxs-lookup"><span data-stu-id="0810a-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0810a-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="0810a-124">ModuleID</span></span>|<span data-ttu-id="0810a-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0810a-125">win:UInt16</span></span>|<span data-ttu-id="0810a-126">モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="0810a-126">The module identifier.</span></span>|  
|<span data-ttu-id="0810a-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="0810a-127">StubMethodID</span></span>|<span data-ttu-id="0810a-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0810a-128">win:UInt64</span></span>|<span data-ttu-id="0810a-129">スタブのメソッド識別子。</span><span class="sxs-lookup"><span data-stu-id="0810a-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="0810a-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="0810a-130">StubFlags</span></span>|<span data-ttu-id="0810a-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0810a-131">win:UInt64</span></span>|<span data-ttu-id="0810a-132">スタブのフラグ:</span><span class="sxs-lookup"><span data-stu-id="0810a-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="0810a-133">0x1 - 逆方向の相互運用。</span><span class="sxs-lookup"><span data-stu-id="0810a-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="0810a-134">0x2 - COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="0810a-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="0810a-135">0x4 - NGen.exe で生成されたスタブ。</span><span class="sxs-lookup"><span data-stu-id="0810a-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="0810a-136">0x8 - デリゲート。</span><span class="sxs-lookup"><span data-stu-id="0810a-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="0810a-137">0x10 - 可変個引数。</span><span class="sxs-lookup"><span data-stu-id="0810a-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="0810a-138">0x20 - アンマネージ呼び出し先。</span><span class="sxs-lookup"><span data-stu-id="0810a-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="0810a-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="0810a-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="0810a-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0810a-140">win:UInt32</span></span>|<span data-ttu-id="0810a-141">マネージ相互運用メソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="0810a-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="0810a-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="0810a-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="0810a-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-143">win:UnicodeString</span></span>|<span data-ttu-id="0810a-144">マネージ相互運用メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="0810a-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="0810a-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="0810a-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="0810a-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-146">win:UnicodeString</span></span>|<span data-ttu-id="0810a-147">マネージ相互運用メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="0810a-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="0810a-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="0810a-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="0810a-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-149">win:UnicodeString</span></span>|<span data-ttu-id="0810a-150">マネージ相互運用メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="0810a-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="0810a-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="0810a-151">NativeMethodSignature</span></span>|<span data-ttu-id="0810a-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-152">win:UnicodeString</span></span>|<span data-ttu-id="0810a-153">ネイティブ メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="0810a-153">The native method signature.</span></span>|  
|<span data-ttu-id="0810a-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="0810a-154">StubMethodSignature</span></span>|<span data-ttu-id="0810a-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-155">win:UnicodeString</span></span>|<span data-ttu-id="0810a-156">スタブ メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="0810a-156">The stub method signature.</span></span>|  
|<span data-ttu-id="0810a-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="0810a-157">StubMethodILCode</span></span>|<span data-ttu-id="0810a-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-158">win:UnicodeString</span></span>|<span data-ttu-id="0810a-159">スタブ メソッドの MSIL コード。</span><span class="sxs-lookup"><span data-stu-id="0810a-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="0810a-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0810a-160">ClrInstanceID</span></span>|<span data-ttu-id="0810a-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0810a-161">win:UInt16</span></span>|<span data-ttu-id="0810a-162">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="0810a-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0810a-163">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0810a-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="0810a-164">ILStubCacheHit イベント</span><span class="sxs-lookup"><span data-stu-id="0810a-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="0810a-165">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="0810a-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0810a-166">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="0810a-166">Keyword for raising the event</span></span>|<span data-ttu-id="0810a-167">レベル</span><span class="sxs-lookup"><span data-stu-id="0810a-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0810a-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="0810a-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="0810a-169">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="0810a-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="0810a-170">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="0810a-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0810a-171">イベント</span><span class="sxs-lookup"><span data-stu-id="0810a-171">Event</span></span>|<span data-ttu-id="0810a-172">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0810a-172">Event ID</span></span>|<span data-ttu-id="0810a-173">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="0810a-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="0810a-174">89</span><span class="sxs-lookup"><span data-stu-id="0810a-174">89</span></span>|<span data-ttu-id="0810a-175">MSIL のキャッシュにアクセスがあった。</span><span class="sxs-lookup"><span data-stu-id="0810a-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="0810a-176">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="0810a-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0810a-177">フィールド名</span><span class="sxs-lookup"><span data-stu-id="0810a-177">Field name</span></span>|<span data-ttu-id="0810a-178">データ型</span><span class="sxs-lookup"><span data-stu-id="0810a-178">Data type</span></span>|<span data-ttu-id="0810a-179">説明</span><span class="sxs-lookup"><span data-stu-id="0810a-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0810a-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="0810a-180">ModuleID</span></span>|<span data-ttu-id="0810a-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0810a-181">win:UInt16</span></span>|<span data-ttu-id="0810a-182">モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="0810a-182">The module identifier.</span></span>|  
|<span data-ttu-id="0810a-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="0810a-183">StubMethodID</span></span>|<span data-ttu-id="0810a-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0810a-184">win:UInt64</span></span>|<span data-ttu-id="0810a-185">スタブのメソッド識別子。</span><span class="sxs-lookup"><span data-stu-id="0810a-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="0810a-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="0810a-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="0810a-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0810a-187">win:UInt32</span></span>|<span data-ttu-id="0810a-188">マネージ相互運用メソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="0810a-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="0810a-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="0810a-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="0810a-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-190">win:UnicodeString</span></span>|<span data-ttu-id="0810a-191">マネージ相互運用メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="0810a-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="0810a-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="0810a-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="0810a-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-193">win:UnicodeString</span></span>|<span data-ttu-id="0810a-194">マネージ相互運用メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="0810a-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="0810a-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="0810a-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="0810a-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0810a-196">win:UnicodeString</span></span>|<span data-ttu-id="0810a-197">マネージ相互運用メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="0810a-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="0810a-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0810a-198">ClrInstanceID</span></span>|<span data-ttu-id="0810a-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0810a-199">win:UInt16</span></span>|<span data-ttu-id="0810a-200">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="0810a-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0810a-201">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0810a-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="0810a-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="0810a-202">See Also</span></span>  
 [<span data-ttu-id="0810a-203">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="0810a-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
