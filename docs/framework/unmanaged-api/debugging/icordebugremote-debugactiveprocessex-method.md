---
title: "ICorDebugRemote::DebugActiveProcessEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09bc98b477231eb1466300451585f4569aff222c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="f247c-102">ICorDebugRemote::DebugActiveProcessEx メソッド</span><span class="sxs-lookup"><span data-stu-id="f247c-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="f247c-103">デバッガーの下でリモート コンピューター上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="f247c-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f247c-104">構文</span><span class="sxs-lookup"><span data-stu-id="f247c-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f247c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f247c-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="f247c-106">[in]ポインター、 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="f247c-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="f247c-107">このパラメーターは使用、プロセスが実行されているコンピューターを決定します。</span><span class="sxs-lookup"><span data-stu-id="f247c-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="f247c-108">[in]デバッガーのアタッチ先となるプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="f247c-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="f247c-109">[in]`true`デバッガーがプロセスの Win32 デバッガーとして動作する必要があります、アンマネージのコールバックのディスパッチ場合はそれ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="f247c-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="f247c-110">[out]デバッガーのアタッチするプロセスを表す"ICorDebugProcess"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f247c-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f247c-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="f247c-111">Return Value</span></span>  
 <span data-ttu-id="f247c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f247c-112">S_OK</span></span>  
 <span data-ttu-id="f247c-113">リモート コンピューター上のプロセスが正常に接続します。</span><span class="sxs-lookup"><span data-stu-id="f247c-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="f247c-114">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="f247c-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f247c-115">リモート コンピューター上のプロセスにアタッチできません。</span><span class="sxs-lookup"><span data-stu-id="f247c-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f247c-116">コメント</span><span class="sxs-lookup"><span data-stu-id="f247c-116">Remarks</span></span>  
 <span data-ttu-id="f247c-117">混合モード デバッグは Silverlight ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f247c-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f247c-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="f247c-118">Requirements</span></span>  
 <span data-ttu-id="f247c-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f247c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f247c-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f247c-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f247c-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f247c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f247c-122">**.NET framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f247c-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f247c-123">参照</span><span class="sxs-lookup"><span data-stu-id="f247c-123">See Also</span></span>  
 [<span data-ttu-id="f247c-124">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f247c-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="f247c-125">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f247c-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="f247c-126">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f247c-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
