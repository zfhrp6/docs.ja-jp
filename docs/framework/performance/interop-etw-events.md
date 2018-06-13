---
title: 相互運用 ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bc9a90e9d889673d8f67e4f9158edebcb65235b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396368"
---
# <a name="interop-etw-events"></a><span data-ttu-id="0aaf3-102">相互運用 ETW イベント</span><span class="sxs-lookup"><span data-stu-id="0aaf3-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="0aaf3-103">相互運用イベントは、Microsoft intermediate language (MSIL) のスタブ生成とキャッシュに関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="0aaf3-104">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="0aaf3-105">ILStubGenerated イベント</span><span class="sxs-lookup"><span data-stu-id="0aaf3-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="0aaf3-106">ILStubCacheHit イベント</span><span class="sxs-lookup"><span data-stu-id="0aaf3-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="0aaf3-107">ILStubGenerated イベント</span><span class="sxs-lookup"><span data-stu-id="0aaf3-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="0aaf3-108">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="0aaf3-109">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0aaf3-110">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="0aaf3-110">Keyword for raising the event</span></span>|<span data-ttu-id="0aaf3-111">レベル</span><span class="sxs-lookup"><span data-stu-id="0aaf3-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0aaf3-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="0aaf3-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="0aaf3-113">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="0aaf3-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="0aaf3-114">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0aaf3-115">イベント</span><span class="sxs-lookup"><span data-stu-id="0aaf3-115">Event</span></span>|<span data-ttu-id="0aaf3-116">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0aaf3-116">Event ID</span></span>|<span data-ttu-id="0aaf3-117">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="0aaf3-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="0aaf3-118">88</span><span class="sxs-lookup"><span data-stu-id="0aaf3-118">88</span></span>|<span data-ttu-id="0aaf3-119">MSIL スタブが生成された。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="0aaf3-120">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0aaf3-121">フィールド名</span><span class="sxs-lookup"><span data-stu-id="0aaf3-121">Field name</span></span>|<span data-ttu-id="0aaf3-122">データ型</span><span class="sxs-lookup"><span data-stu-id="0aaf3-122">Data type</span></span>|<span data-ttu-id="0aaf3-123">説明</span><span class="sxs-lookup"><span data-stu-id="0aaf3-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0aaf3-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="0aaf3-124">ModuleID</span></span>|<span data-ttu-id="0aaf3-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0aaf3-125">win:UInt16</span></span>|<span data-ttu-id="0aaf3-126">モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-126">The module identifier.</span></span>|  
|<span data-ttu-id="0aaf3-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="0aaf3-127">StubMethodID</span></span>|<span data-ttu-id="0aaf3-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0aaf3-128">win:UInt64</span></span>|<span data-ttu-id="0aaf3-129">スタブのメソッド識別子。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="0aaf3-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="0aaf3-130">StubFlags</span></span>|<span data-ttu-id="0aaf3-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0aaf3-131">win:UInt64</span></span>|<span data-ttu-id="0aaf3-132">スタブのフラグ:</span><span class="sxs-lookup"><span data-stu-id="0aaf3-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="0aaf3-133">0x1 - 逆方向の相互運用。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="0aaf3-134">0x2 - COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="0aaf3-135">0x4 - NGen.exe で生成されたスタブ。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="0aaf3-136">0x8 - デリゲート。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="0aaf3-137">0x10 - 可変個引数。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="0aaf3-138">0x20 - アンマネージ呼び出し先。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="0aaf3-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="0aaf3-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="0aaf3-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0aaf3-140">win:UInt32</span></span>|<span data-ttu-id="0aaf3-141">マネージ相互運用メソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="0aaf3-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="0aaf3-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="0aaf3-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-143">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-144">マネージ相互運用メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="0aaf3-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="0aaf3-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="0aaf3-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-146">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-147">マネージ相互運用メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="0aaf3-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="0aaf3-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="0aaf3-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-149">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-150">マネージ相互運用メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="0aaf3-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="0aaf3-151">NativeMethodSignature</span></span>|<span data-ttu-id="0aaf3-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-152">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-153">ネイティブ メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-153">The native method signature.</span></span>|  
|<span data-ttu-id="0aaf3-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="0aaf3-154">StubMethodSignature</span></span>|<span data-ttu-id="0aaf3-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-155">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-156">スタブ メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-156">The stub method signature.</span></span>|  
|<span data-ttu-id="0aaf3-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="0aaf3-157">StubMethodILCode</span></span>|<span data-ttu-id="0aaf3-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-158">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-159">スタブ メソッドの MSIL コード。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="0aaf3-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0aaf3-160">ClrInstanceID</span></span>|<span data-ttu-id="0aaf3-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0aaf3-161">win:UInt16</span></span>|<span data-ttu-id="0aaf3-162">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0aaf3-163">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0aaf3-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="0aaf3-164">ILStubCacheHit イベント</span><span class="sxs-lookup"><span data-stu-id="0aaf3-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="0aaf3-165">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0aaf3-166">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="0aaf3-166">Keyword for raising the event</span></span>|<span data-ttu-id="0aaf3-167">レベル</span><span class="sxs-lookup"><span data-stu-id="0aaf3-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0aaf3-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="0aaf3-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="0aaf3-169">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="0aaf3-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="0aaf3-170">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0aaf3-171">イベント</span><span class="sxs-lookup"><span data-stu-id="0aaf3-171">Event</span></span>|<span data-ttu-id="0aaf3-172">イベント ID</span><span class="sxs-lookup"><span data-stu-id="0aaf3-172">Event ID</span></span>|<span data-ttu-id="0aaf3-173">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="0aaf3-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="0aaf3-174">89</span><span class="sxs-lookup"><span data-stu-id="0aaf3-174">89</span></span>|<span data-ttu-id="0aaf3-175">MSIL のキャッシュにアクセスがあった。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="0aaf3-176">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0aaf3-177">フィールド名</span><span class="sxs-lookup"><span data-stu-id="0aaf3-177">Field name</span></span>|<span data-ttu-id="0aaf3-178">データ型</span><span class="sxs-lookup"><span data-stu-id="0aaf3-178">Data type</span></span>|<span data-ttu-id="0aaf3-179">説明</span><span class="sxs-lookup"><span data-stu-id="0aaf3-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0aaf3-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="0aaf3-180">ModuleID</span></span>|<span data-ttu-id="0aaf3-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0aaf3-181">win:UInt16</span></span>|<span data-ttu-id="0aaf3-182">モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-182">The module identifier.</span></span>|  
|<span data-ttu-id="0aaf3-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="0aaf3-183">StubMethodID</span></span>|<span data-ttu-id="0aaf3-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0aaf3-184">win:UInt64</span></span>|<span data-ttu-id="0aaf3-185">スタブのメソッド識別子。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="0aaf3-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="0aaf3-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="0aaf3-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0aaf3-187">win:UInt32</span></span>|<span data-ttu-id="0aaf3-188">マネージ相互運用メソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="0aaf3-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="0aaf3-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="0aaf3-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-190">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-191">マネージ相互運用メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="0aaf3-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="0aaf3-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="0aaf3-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-193">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-194">マネージ相互運用メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="0aaf3-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="0aaf3-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="0aaf3-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0aaf3-196">win:UnicodeString</span></span>|<span data-ttu-id="0aaf3-197">マネージ相互運用メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="0aaf3-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0aaf3-198">ClrInstanceID</span></span>|<span data-ttu-id="0aaf3-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0aaf3-199">win:UInt16</span></span>|<span data-ttu-id="0aaf3-200">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="0aaf3-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0aaf3-201">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="0aaf3-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="0aaf3-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="0aaf3-202">See Also</span></span>  
 [<span data-ttu-id="0aaf3-203">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="0aaf3-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
