---
title: "列挙体のデバッグ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5e294275da45575a3aed457fb2428c4768e78d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-enumerations"></a><span data-ttu-id="f8379-102">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f8379-102">Debugging Enumerations</span></span>
<span data-ttu-id="f8379-103">このセクションでは、デバッグ API が使用するアンマネージ列挙体について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8379-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8379-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f8379-104">In This Section</span></span>  
 [<span data-ttu-id="f8379-105">CLR_DEBUGGING_PROCESS_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="f8379-106">によって使用されている値を提供、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f8379-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="f8379-107">CLRDataEnumMemoryFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="f8379-108">メモリ領域への呼び出しを示す、 [iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)メソッドに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8379-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="f8379-109">COR_PUB_ENUMPROCESS 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="f8379-110">列挙するプロセスの型を識別します。</span><span class="sxs-lookup"><span data-stu-id="f8379-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="f8379-111">CorDebugBlockingReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="f8379-112">指定されたオブジェクト上でスレッドがブロックされる理由を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8379-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="f8379-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="f8379-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="f8379-114">呼び出しチェーンが開始する理由を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="f8379-115">CorDebugCodeInvokeKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="f8379-116">エクスポートされた関数がマネージ コードを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="f8379-117">CorDebugCodeInvokePurpose 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="f8379-118">エクスポートされた関数がマネージ コードを呼び出す理由を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="f8379-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="f8379-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="f8379-120">呼び出しで使用できる追加のデバッグ オプションを提供、 [icordebug::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f8379-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="f8379-121">CorDebugDebugEventKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="f8379-122">情報がデコードされるによってイベントの種類を示す、 [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f8379-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="f8379-123">CorDebugDecodeEventFlagsWindows 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="f8379-124">Windows プラットフォームのデバッグ イベントに関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f8379-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="f8379-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="f8379-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="f8379-126">指定されたコールバックの型を示す、 [icordebugmanagedcallback 2::exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)イベント。</span><span class="sxs-lookup"><span data-stu-id="f8379-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="f8379-127">CorDebugExceptionFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="f8379-128">例外に関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f8379-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="f8379-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="f8379-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="f8379-130">アンワインド フェーズ中にコールバックによって通知されるイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="f8379-131">CorDebugGCType 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="f8379-132">ガベージ コレクターがワークステーションまたはサーバーのどちらで実行されているかを示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="f8379-133">CorDebugGenerationTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="f8379-134">マネージ ヒープ上のメモリ領域の生成を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8379-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="f8379-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="f8379-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="f8379-136">ハンドル型を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="f8379-137">CorDebugIlToNativeMappingTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="f8379-138">ネイティブ命令の特定の範囲が特別なコード領域に対応するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="f8379-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="f8379-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="f8379-140">ステップ インできるコードの型を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="f8379-141">CorDebugInterfaceVersion 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="f8379-142">.NET Framework のバージョン、またはインターフェイスが導入された .NET Framework のバージョンのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8379-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="f8379-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="f8379-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="f8379-144">スタック フレームの型を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="f8379-145">CorDebugJITCompilerFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="f8379-146">マネージ Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f8379-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="f8379-147">CorDebugJITCompilerFlagsDeprecated 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="f8379-148">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f8379-148">Obsolete.</span></span> <span data-ttu-id="f8379-149">使用して、`CORDEBUG_JIT_DEFAULT`のメンバー、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列挙代わりにします。</span><span class="sxs-lookup"><span data-stu-id="f8379-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="f8379-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="f8379-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="f8379-151">命令ポインター (IP) の値が得られた方法の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="f8379-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="f8379-152">CorDebugMDAFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="f8379-153">マネージ デバッグ アシスタント (MDA) が生成されるスレッドのステータスを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8379-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="f8379-154">CorDebugNGenPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="f8379-155">デバッガーがネイティブ イメージ キャッシュからネイティブ (NGen) イメージを読み込むかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="f8379-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="f8379-156">CorDebugPlatform 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="f8379-157">使用されるターゲット プラットフォームの値を提供、 [icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f8379-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="f8379-158">CorDebugRecordFormat 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="f8379-159">ネイティブ例外デバッグ イベントに関する情報を格納するバイト配列内のデータの形式を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="f8379-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="f8379-160">CorDebugRegister</span></span>  
 <span data-ttu-id="f8379-161">指定されたプロセッサ アーキテクチャに関連付けられたレジスタを指定します。</span><span class="sxs-lookup"><span data-stu-id="f8379-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="f8379-162">CorDebugSetContextFlag 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="f8379-163">スタック上のアクティブ (またはリーフ) フレーム上からのコンテキストなのか、別のフレームからのアンワインドにより計算されたコンテキストなのかを示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="f8379-164">CorDebugStateChange 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="f8379-165">プロセスへの変更に基づいて破棄が必要となった、キャッシュされたデータの量を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="f8379-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="f8379-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="f8379-167">個々のステップの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="f8379-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="f8379-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="f8379-169">デバッグのスレッドの状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8379-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="f8379-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="f8379-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="f8379-171">ステッパによるコード実行の停止をトリガーする可能性のあるマップ解除したコードの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8379-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="f8379-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="f8379-172">CorDebugUserState</span></span>  
 <span data-ttu-id="f8379-173">スレッドのユーザーの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="f8379-174">CorGCReferenceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="f8379-175">ガベージ コレクトされる必要のあるオブジェクトのソースを識別します。</span><span class="sxs-lookup"><span data-stu-id="f8379-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="f8379-176">ILCodeKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="f8379-177">デバッガーがローカル変数またはプロファイラー ReJIT インストルメンテーションに追加されたコードにアクセスできるかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="f8379-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="f8379-178">LoggingLevelEnum 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="f8379-179">マネージ スレッドがイベントを記録する際にイベント ログに書き込まれる説明メッセージの重大度レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="f8379-180">LogSwitchCallReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="f8379-181">デバッグとトレースの切り替えで実行された操作を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="f8379-182">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="f8379-183">変数のネイティブの場所の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="f8379-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="f8379-184">WriteableMetadataUpdateMode 列挙型</span><span class="sxs-lookup"><span data-stu-id="f8379-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="f8379-185">メモリ内のメタデータ更新をデバッガーに対して可視にするかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="f8379-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f8379-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8379-186">Related Sections</span></span>  
 [<span data-ttu-id="f8379-187">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="f8379-187">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="f8379-188">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8379-188">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="f8379-189">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="f8379-189">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="f8379-190">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="f8379-190">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
