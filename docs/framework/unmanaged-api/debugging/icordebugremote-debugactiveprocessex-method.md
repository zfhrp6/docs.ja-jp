---
title: ICorDebugRemote::DebugActiveProcessEx メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e3cdbff5054ec990c40c333ed4bd4029a91f12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420805"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="49718-102">ICorDebugRemote::DebugActiveProcessEx メソッド</span><span class="sxs-lookup"><span data-stu-id="49718-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="49718-103">デバッガーの下でリモート コンピューター上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="49718-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49718-104">構文</span><span class="sxs-lookup"><span data-stu-id="49718-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49718-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49718-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="49718-106">[in]ポインター、 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="49718-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="49718-107">このパラメーターは使用、プロセスが実行されているコンピューターを決定します。</span><span class="sxs-lookup"><span data-stu-id="49718-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="49718-108">[in]デバッガーのアタッチ先となるプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="49718-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="49718-109">[in]`true`デバッガーがプロセスの Win32 デバッガーとして動作する必要があります、アンマネージのコールバックのディスパッチ場合はそれ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="49718-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="49718-110">[out]デバッガーのアタッチするプロセスを表す"ICorDebugProcess"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="49718-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49718-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="49718-111">Return Value</span></span>  
 <span data-ttu-id="49718-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="49718-112">S_OK</span></span>  
 <span data-ttu-id="49718-113">リモート コンピューター上のプロセスが正常に接続します。</span><span class="sxs-lookup"><span data-stu-id="49718-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="49718-114">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="49718-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="49718-115">リモート コンピューター上のプロセスにアタッチできません。</span><span class="sxs-lookup"><span data-stu-id="49718-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49718-116">コメント</span><span class="sxs-lookup"><span data-stu-id="49718-116">Remarks</span></span>  
 <span data-ttu-id="49718-117">混合モード デバッグは Silverlight ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="49718-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49718-118">要件</span><span class="sxs-lookup"><span data-stu-id="49718-118">Requirements</span></span>  
 <span data-ttu-id="49718-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="49718-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49718-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49718-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49718-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49718-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49718-122">**.NET framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="49718-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49718-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="49718-123">See Also</span></span>  
 [<span data-ttu-id="49718-124">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49718-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="49718-125">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49718-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="49718-126">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49718-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
