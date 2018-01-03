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
ms.workload: dotnet
ms.openlocfilehash: e5670eb910406626096f776d3b4192e2d58d7ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="7869d-102">相互運用 ETW イベント</span><span class="sxs-lookup"><span data-stu-id="7869d-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="7869d-103">相互運用イベントは、Microsoft intermediate language (MSIL) のスタブ生成とキャッシュに関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="7869d-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="7869d-104">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="7869d-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="7869d-105">ILStubGenerated イベント</span><span class="sxs-lookup"><span data-stu-id="7869d-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="7869d-106">ILStubCacheHit イベント</span><span class="sxs-lookup"><span data-stu-id="7869d-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="7869d-107">ILStubGenerated イベント</span><span class="sxs-lookup"><span data-stu-id="7869d-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="7869d-108">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="7869d-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="7869d-109">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="7869d-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="7869d-110">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="7869d-110">Keyword for raising the event</span></span>|<span data-ttu-id="7869d-111">レベル</span><span class="sxs-lookup"><span data-stu-id="7869d-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7869d-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="7869d-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="7869d-113">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7869d-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="7869d-114">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="7869d-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7869d-115">イベント</span><span class="sxs-lookup"><span data-stu-id="7869d-115">Event</span></span>|<span data-ttu-id="7869d-116">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7869d-116">Event ID</span></span>|<span data-ttu-id="7869d-117">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="7869d-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="7869d-118">88</span><span class="sxs-lookup"><span data-stu-id="7869d-118">88</span></span>|<span data-ttu-id="7869d-119">MSIL スタブが生成された。</span><span class="sxs-lookup"><span data-stu-id="7869d-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="7869d-120">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="7869d-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7869d-121">フィールド名</span><span class="sxs-lookup"><span data-stu-id="7869d-121">Field name</span></span>|<span data-ttu-id="7869d-122">データ型</span><span class="sxs-lookup"><span data-stu-id="7869d-122">Data type</span></span>|<span data-ttu-id="7869d-123">説明</span><span class="sxs-lookup"><span data-stu-id="7869d-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7869d-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="7869d-124">ModuleID</span></span>|<span data-ttu-id="7869d-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7869d-125">win:UInt16</span></span>|<span data-ttu-id="7869d-126">モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="7869d-126">The module identifier.</span></span>|  
|<span data-ttu-id="7869d-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="7869d-127">StubMethodID</span></span>|<span data-ttu-id="7869d-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7869d-128">win:UInt64</span></span>|<span data-ttu-id="7869d-129">スタブのメソッド識別子。</span><span class="sxs-lookup"><span data-stu-id="7869d-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="7869d-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="7869d-130">StubFlags</span></span>|<span data-ttu-id="7869d-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7869d-131">win:UInt64</span></span>|<span data-ttu-id="7869d-132">スタブのフラグ:</span><span class="sxs-lookup"><span data-stu-id="7869d-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="7869d-133">0x1 - 逆方向の相互運用。</span><span class="sxs-lookup"><span data-stu-id="7869d-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="7869d-134">0x2 - COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="7869d-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="7869d-135">0x4 - NGen.exe で生成されたスタブ。</span><span class="sxs-lookup"><span data-stu-id="7869d-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="7869d-136">0x8 - デリゲート。</span><span class="sxs-lookup"><span data-stu-id="7869d-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="7869d-137">0x10 - 可変個引数。</span><span class="sxs-lookup"><span data-stu-id="7869d-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="7869d-138">0x20 - アンマネージ呼び出し先。</span><span class="sxs-lookup"><span data-stu-id="7869d-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="7869d-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="7869d-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="7869d-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7869d-140">win:UInt32</span></span>|<span data-ttu-id="7869d-141">マネージ相互運用メソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="7869d-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="7869d-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="7869d-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="7869d-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-143">win:UnicodeString</span></span>|<span data-ttu-id="7869d-144">マネージ相互運用メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="7869d-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="7869d-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="7869d-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="7869d-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-146">win:UnicodeString</span></span>|<span data-ttu-id="7869d-147">マネージ相互運用メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="7869d-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="7869d-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="7869d-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="7869d-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-149">win:UnicodeString</span></span>|<span data-ttu-id="7869d-150">マネージ相互運用メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="7869d-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="7869d-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="7869d-151">NativeMethodSignature</span></span>|<span data-ttu-id="7869d-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-152">win:UnicodeString</span></span>|<span data-ttu-id="7869d-153">ネイティブ メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="7869d-153">The native method signature.</span></span>|  
|<span data-ttu-id="7869d-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="7869d-154">StubMethodSignature</span></span>|<span data-ttu-id="7869d-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-155">win:UnicodeString</span></span>|<span data-ttu-id="7869d-156">スタブ メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="7869d-156">The stub method signature.</span></span>|  
|<span data-ttu-id="7869d-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="7869d-157">StubMethodILCode</span></span>|<span data-ttu-id="7869d-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-158">win:UnicodeString</span></span>|<span data-ttu-id="7869d-159">スタブ メソッドの MSIL コード。</span><span class="sxs-lookup"><span data-stu-id="7869d-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="7869d-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7869d-160">ClrInstanceID</span></span>|<span data-ttu-id="7869d-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7869d-161">win:UInt16</span></span>|<span data-ttu-id="7869d-162">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="7869d-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7869d-163">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="7869d-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="7869d-164">ILStubCacheHit イベント</span><span class="sxs-lookup"><span data-stu-id="7869d-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="7869d-165">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="7869d-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7869d-166">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="7869d-166">Keyword for raising the event</span></span>|<span data-ttu-id="7869d-167">レベル</span><span class="sxs-lookup"><span data-stu-id="7869d-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7869d-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="7869d-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="7869d-169">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7869d-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="7869d-170">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="7869d-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7869d-171">イベント</span><span class="sxs-lookup"><span data-stu-id="7869d-171">Event</span></span>|<span data-ttu-id="7869d-172">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7869d-172">Event ID</span></span>|<span data-ttu-id="7869d-173">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="7869d-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="7869d-174">89</span><span class="sxs-lookup"><span data-stu-id="7869d-174">89</span></span>|<span data-ttu-id="7869d-175">MSIL のキャッシュにアクセスがあった。</span><span class="sxs-lookup"><span data-stu-id="7869d-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="7869d-176">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="7869d-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7869d-177">フィールド名</span><span class="sxs-lookup"><span data-stu-id="7869d-177">Field name</span></span>|<span data-ttu-id="7869d-178">データ型</span><span class="sxs-lookup"><span data-stu-id="7869d-178">Data type</span></span>|<span data-ttu-id="7869d-179">説明</span><span class="sxs-lookup"><span data-stu-id="7869d-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7869d-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="7869d-180">ModuleID</span></span>|<span data-ttu-id="7869d-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7869d-181">win:UInt16</span></span>|<span data-ttu-id="7869d-182">モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="7869d-182">The module identifier.</span></span>|  
|<span data-ttu-id="7869d-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="7869d-183">StubMethodID</span></span>|<span data-ttu-id="7869d-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7869d-184">win:UInt64</span></span>|<span data-ttu-id="7869d-185">スタブのメソッド識別子。</span><span class="sxs-lookup"><span data-stu-id="7869d-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="7869d-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="7869d-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="7869d-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7869d-187">win:UInt32</span></span>|<span data-ttu-id="7869d-188">マネージ相互運用メソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="7869d-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="7869d-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="7869d-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="7869d-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-190">win:UnicodeString</span></span>|<span data-ttu-id="7869d-191">マネージ相互運用メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="7869d-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="7869d-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="7869d-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="7869d-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-193">win:UnicodeString</span></span>|<span data-ttu-id="7869d-194">マネージ相互運用メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="7869d-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="7869d-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="7869d-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="7869d-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7869d-196">win:UnicodeString</span></span>|<span data-ttu-id="7869d-197">マネージ相互運用メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="7869d-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="7869d-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7869d-198">ClrInstanceID</span></span>|<span data-ttu-id="7869d-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7869d-199">win:UInt16</span></span>|<span data-ttu-id="7869d-200">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="7869d-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7869d-201">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="7869d-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="7869d-202">参照</span><span class="sxs-lookup"><span data-stu-id="7869d-202">See Also</span></span>  
 [<span data-ttu-id="7869d-203">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="7869d-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
