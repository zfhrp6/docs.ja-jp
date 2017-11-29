---
title: "ICorDebugRemote インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemote
helpviewer_keywords: ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6195b53d11877c6b7b2a52c3fd8d194dfb51810
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="183bc-102">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="183bc-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="183bc-103">リモート ターゲット プロセスに対してマネージ デバッガーを起動または接続する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="183bc-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="183bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="183bc-104">Syntax</span></span>  
  
```  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="183bc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="183bc-105">Methods</span></span>  
  
|<span data-ttu-id="183bc-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="183bc-106">Method</span></span>|<span data-ttu-id="183bc-107">説明</span><span class="sxs-lookup"><span data-stu-id="183bc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="183bc-108">Icordebugremote::createprocessex メソッド</span><span class="sxs-lookup"><span data-stu-id="183bc-108">ICorDebugRemote::CreateProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-createprocessex-method.md)|<span data-ttu-id="183bc-109">マネージ デバッグのために、リモート コンピューターでプロセスを作成します。</span><span class="sxs-lookup"><span data-stu-id="183bc-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="183bc-110">Icordebugremote::debugactiveprocessex メソッド</span><span class="sxs-lookup"><span data-stu-id="183bc-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="183bc-111">デバッガーの下でリモート コンピューター上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="183bc-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="183bc-112">コメント</span><span class="sxs-lookup"><span data-stu-id="183bc-112">Remarks</span></span>  
 <span data-ttu-id="183bc-113">現在、この機能はサポートされてのみリモート Macintosh コンピューターで実行されている Silverlight ベースのアプリケーションのターゲットをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="183bc-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="183bc-114">要件</span><span class="sxs-lookup"><span data-stu-id="183bc-114">Requirements</span></span>  
 <span data-ttu-id="183bc-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="183bc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="183bc-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="183bc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="183bc-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="183bc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="183bc-118">**.NET framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="183bc-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183bc-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="183bc-119">See Also</span></span>  
 [<span data-ttu-id="183bc-120">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="183bc-120">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="183bc-121">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="183bc-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="183bc-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="183bc-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
