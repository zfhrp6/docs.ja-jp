---
title: ICorDebugModule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ced01c9c01a32468f371a8e172c878337fb79757
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="c0bfc-102">ICorDebugModule Interface1</span><span class="sxs-lookup"><span data-stu-id="c0bfc-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="c0bfc-103">共通言語ランタイム (CLR) モジュールは、実行可能ファイルかダイナミック リンク ライブラリ (DLL) を表します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0bfc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-104">Methods</span></span>  
  
|<span data-ttu-id="c0bfc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-105">Method</span></span>|<span data-ttu-id="c0bfc-106">説明</span><span class="sxs-lookup"><span data-stu-id="c0bfc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0bfc-107">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="c0bfc-108">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-108">Not implemented.</span></span>|  
|[<span data-ttu-id="c0bfc-109">EnableClassLoadCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="c0bfc-110">決定するかどうか、 [icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)と[icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)このモジュールのコールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="c0bfc-111">EnableJITDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="c0bfc-112">・ イン タイム (JIT) コンパイラがこのモジュール内でメソッドのデバッグ情報を保持するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="c0bfc-113">GetAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="c0bfc-114">このモジュールを含むアセンブリを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="c0bfc-115">GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="c0bfc-116">モジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="c0bfc-117">GetClassFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="c0bfc-118">メタデータから、ICorDebugClass を取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="c0bfc-119">GetEditAndContinueSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="c0bfc-120">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-120">Deprecated.</span></span>|  
|[<span data-ttu-id="c0bfc-121">GetFunctionFromRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="c0bfc-122">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-122">Not implemented.</span></span>|  
|[<span data-ttu-id="c0bfc-123">GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="c0bfc-124">メタデータ トークンによって指定された関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="c0bfc-125">GetGlobalVariableValue メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="c0bfc-126">指定のグローバル変数の値のオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="c0bfc-127">GetMetaDataInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="c0bfc-128">モジュールのメタデータの検査に使用できるメタデータ インターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="c0bfc-129">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="c0bfc-130">モジュールのファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="c0bfc-131">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="c0bfc-132">このモジュールに格納しているプロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="c0bfc-133">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="c0bfc-134">モジュールのサイズをバイト単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="c0bfc-135">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="c0bfc-136">このモジュールのテーブルのエントリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="c0bfc-137">IsDynamic メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="c0bfc-138">モジュールが動的かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="c0bfc-139">IsInMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="c0bfc-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="c0bfc-140">このモジュールは、メモリ内にのみ存在するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0bfc-141">コメント</span><span class="sxs-lookup"><span data-stu-id="c0bfc-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0bfc-142">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0bfc-143">要件</span><span class="sxs-lookup"><span data-stu-id="c0bfc-143">Requirements</span></span>  
 <span data-ttu-id="c0bfc-144">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0bfc-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0bfc-145">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0bfc-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0bfc-146">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0bfc-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0bfc-147">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0bfc-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0bfc-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0bfc-148">See Also</span></span>  
 [<span data-ttu-id="c0bfc-149">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0bfc-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="c0bfc-150">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0bfc-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)