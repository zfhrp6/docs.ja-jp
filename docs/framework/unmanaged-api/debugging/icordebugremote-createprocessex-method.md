---
title: "ICorDebugRemote::CreateProcessEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote.CreateProcessEx
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25c6e8455bf5154a841d302a7f97db8f5ce0c381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="a1afc-102">ICorDebugRemote::CreateProcessEx メソッド</span><span class="sxs-lookup"><span data-stu-id="a1afc-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="a1afc-103">デバッガーの下でリモート コンピューター上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="a1afc-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1afc-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1afc-104">Syntax</span></span>  
  
```  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1afc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1afc-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="a1afc-106">[in]ポインター、 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="a1afc-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="a1afc-107">プロセスを起動するリモート コンピューターを決定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a1afc-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="a1afc-108">[in]実行中のプロセスによって実行されるモジュールを指定する null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a1afc-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="a1afc-109">モジュールは、呼び出し元のプロセスのセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a1afc-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="a1afc-110">[in]実行中のプロセスによって実行されるコマンドラインを指定する null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a1afc-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="a1afc-111">[in]リモート デバッグは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="a1afc-112">[in]リモート デバッグは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="a1afc-113">[in]リモート デバッグは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="a1afc-114">[in]リモート デバッグは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="a1afc-115">[in]新しいプロセスの環境ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a1afc-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="a1afc-116">[in]プロセスの現在のディレクトリへの完全パスを指定する null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a1afc-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="a1afc-117">このパラメーターが null の場合、新しいプロセスは、呼び出し元プロセスとして同じ現在のドライブとディレクトリがあります。</span><span class="sxs-lookup"><span data-stu-id="a1afc-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="a1afc-118">[in]リモート デバッグは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="a1afc-119">[in]リモート デバッグは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="a1afc-120">[in]リモート デバッグは使用しません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a1afc-121">[out]プロセスを表す「ICorDebugProcess インターフェイス」オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a1afc-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1afc-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1afc-122">Return Value</span></span>  
 <span data-ttu-id="a1afc-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1afc-123">S_OK</span></span>  
 <span data-ttu-id="a1afc-124">正常にデバッグするため、リモート コンピューターと返される「ICorDebugProcess インターフェイス」上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="a1afc-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="a1afc-125">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="a1afc-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a1afc-126">リモート コンピューター上のプロセスを起動し、デバッグに「ICorDebugProcess インターフェイス」を返すことができません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1afc-127">コメント</span><span class="sxs-lookup"><span data-stu-id="a1afc-127">Remarks</span></span>  
 <span data-ttu-id="a1afc-128">混合モード デバッグは Silverlight ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a1afc-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1afc-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="a1afc-129">Requirements</span></span>  
 <span data-ttu-id="a1afc-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a1afc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1afc-131">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="a1afc-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="a1afc-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1afc-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1afc-133">**.NET framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a1afc-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1afc-134">参照</span><span class="sxs-lookup"><span data-stu-id="a1afc-134">See Also</span></span>  
 [<span data-ttu-id="a1afc-135">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1afc-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="a1afc-136">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1afc-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="a1afc-137">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1afc-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
