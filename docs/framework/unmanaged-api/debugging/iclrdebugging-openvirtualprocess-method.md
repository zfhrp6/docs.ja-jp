---
title: "ICLRDebugging::OpenVirtualProcess メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging.OpenVirtualProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a59d676e358b2e06ac04bdf586d8ad416445337
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="5ed47-102">ICLRDebugging::OpenVirtualProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="5ed47-102">ICLRDebugging::OpenVirtualProcess Method</span></span>
<span data-ttu-id="5ed47-103">プロセスに読み込まれている共通言語ランタイム (CLR) モジュールに対応する ICorDebugProcess インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ed47-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed47-104">構文</span><span class="sxs-lookup"><span data-stu-id="5ed47-104">Syntax</span></span>  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ed47-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ed47-105">Parameters</span></span>  
 `moduleBaseAddress`  
 <span data-ttu-id="5ed47-106">[in]ターゲット プロセスのモジュールのベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="5ed47-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="5ed47-107">COR_E_NOT_CLR が、指定されたモジュールが CLR モジュールではない場合に返されます。</span><span class="sxs-lookup"><span data-stu-id="5ed47-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="5ed47-108">[in]データ ターゲットの抽象化により、マネージ デバッガーをプロセスの状態を検査します。</span><span class="sxs-lookup"><span data-stu-id="5ed47-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="5ed47-109">デバッガーを実装する必要があります、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5ed47-109">The debugger must implement the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="5ed47-110">実装する必要があります、 [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)ここでは、デバッグ中、CLR がインストールされていないローカル コンピューター上のシナリオをサポートするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5ed47-110">You should implement the [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="5ed47-111">[in]ライブラリ プロバイダー コールバック インターフェイスを上にロードし、要求時にデバッグ ライブラリのバージョンに固有です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="5ed47-112">このパラメーターは必要な場合にのみ`ppProcess`または`pFlags`は`null`します。</span><span class="sxs-lookup"><span data-stu-id="5ed47-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="5ed47-113">[in]このデバッガーをデバッグできる CLR の最高のバージョン。</span><span class="sxs-lookup"><span data-stu-id="5ed47-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="5ed47-114">メジャー、マイナー、を指定して、このデバッガーをサポートする最新の CLR バージョンからのバージョンをビルドしリビジョン番号を将来のインプレース CLR サービス リリースに合わせて 65535 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed47-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="5ed47-115">[in]取得する ICorDebugProcess インターフェイスの ID。</span><span class="sxs-lookup"><span data-stu-id="5ed47-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="5ed47-116">現時点では、可能な値は、IID_CORDEBUGPROCESS3、IID_CORDEBUGPROCESS2、IID_CORDEBUGPROCESS です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="5ed47-117">[out]によって識別される COM インターフェイスへのポインター`riidProcess`です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="5ed47-118">[入力、出力].CLR のバージョン。</span><span class="sxs-lookup"><span data-stu-id="5ed47-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="5ed47-119">この値は、入力で`null`です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-119">On input, this value can be `null`.</span></span> <span data-ttu-id="5ed47-120">指していることも、 [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)構造体、その場合は、構造体の`wStructVersion`0 (ゼロ) にフィールドを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ed47-120">It can also point to a [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="5ed47-121">出力では、返された`CLR_DEBUGGING_VERSION`構造体は、CLR のバージョン情報を使用して入力されます。</span><span class="sxs-lookup"><span data-stu-id="5ed47-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="5ed47-122">[out]指定したランタイムの概要情報のフラグです。</span><span class="sxs-lookup"><span data-stu-id="5ed47-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="5ed47-123">参照してください、 [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)フラグの詳細についてはトピックです。</span><span class="sxs-lookup"><span data-stu-id="5ed47-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ed47-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="5ed47-124">Return Value</span></span>  
 <span data-ttu-id="5ed47-125">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="5ed47-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5ed47-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ed47-126">HRESULT</span></span>|<span data-ttu-id="5ed47-127">説明</span><span class="sxs-lookup"><span data-stu-id="5ed47-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ed47-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ed47-128">S_OK</span></span>|<span data-ttu-id="5ed47-129">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="5ed47-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="5ed47-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5ed47-130">E_POINTER</span></span>|<span data-ttu-id="5ed47-131">`pDataTarget` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="5ed47-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="5ed47-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="5ed47-133">[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)コールバックがエラーを返しますまたは、有効なハンドルは提供されません。</span><span class="sxs-lookup"><span data-stu-id="5ed47-133">The [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="5ed47-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="5ed47-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="5ed47-135">`pDataTarget`このバージョンのランタイムの必要なデータ ターゲットのインターフェイスを実装しません。</span><span class="sxs-lookup"><span data-stu-id="5ed47-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="5ed47-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="5ed47-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="5ed47-137">指定されたモジュールが CLR モジュールではありません。</span><span class="sxs-lookup"><span data-stu-id="5ed47-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="5ed47-138">メモリが破損している、モジュールが使用できないか、CLR バージョン shim バージョンより新しいために、CLR モジュールを検出できない場合にも、この HRESULT が返されます。</span><span class="sxs-lookup"><span data-stu-id="5ed47-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="5ed47-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="5ed47-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="5ed47-140">このランタイムのバージョンは、このデバッグ モデルをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5ed47-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="5ed47-141">現在、デバッグ モデルは前に、のバージョンの CLR でサポートされていません、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-141">Currently, the debugging model is not supported by CLR versions before the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="5ed47-142">`pwszVersion`出力パラメーターが設定されている適切な値にこのエラーが発生後します。</span><span class="sxs-lookup"><span data-stu-id="5ed47-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="5ed47-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="5ed47-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="5ed47-144">CLR のバージョンは、このデバッガーでサポートされるバージョンを超えています。</span><span class="sxs-lookup"><span data-stu-id="5ed47-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="5ed47-145">`pwszVersion`出力パラメーターが設定されている適切な値にこのエラーが発生後します。</span><span class="sxs-lookup"><span data-stu-id="5ed47-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="5ed47-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="5ed47-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="5ed47-147">`riidProcess`インターフェイスは利用できません。</span><span class="sxs-lookup"><span data-stu-id="5ed47-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="5ed47-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="5ed47-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="5ed47-149">`CLR_DEBUGGING_VERSION`構造に認識されている値を持たない`wStructVersion`です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="5ed47-150">この時点でのみ指定できる値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="5ed47-151">例外</span><span class="sxs-lookup"><span data-stu-id="5ed47-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ed47-152">コメント</span><span class="sxs-lookup"><span data-stu-id="5ed47-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed47-153">要件</span><span class="sxs-lookup"><span data-stu-id="5ed47-153">Requirements</span></span>  
 <span data-ttu-id="5ed47-154">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ed47-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed47-155">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ed47-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ed47-156">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ed47-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ed47-157">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed47-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed47-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ed47-158">See Also</span></span>  
 [<span data-ttu-id="5ed47-159">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ed47-159">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5ed47-160">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5ed47-160">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
