---
title: ICorDebugController::Terminate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7a95f09d1baebed65bae994550431d88ba0dfc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="c6239-102">ICorDebugController::Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="c6239-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="c6239-103">指定した終了コードを使用して、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="c6239-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6239-104">このメソッドは、Win32 のラッパー`TerminateProcess`関数。</span><span class="sxs-lookup"><span data-stu-id="c6239-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="c6239-105">したがって、 `Terminate` 、同じ終了コードを使用する Win32`TerminateProcess`関数では使用します。</span><span class="sxs-lookup"><span data-stu-id="c6239-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6239-106">構文</span><span class="sxs-lookup"><span data-stu-id="c6239-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6239-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6239-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="c6239-108">[in]終了コードを示す数値。</span><span class="sxs-lookup"><span data-stu-id="c6239-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="c6239-109">有効な数値の値は、Winbase.h で定義されます。</span><span class="sxs-lookup"><span data-stu-id="c6239-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6239-110">コメント</span><span class="sxs-lookup"><span data-stu-id="c6239-110">Remarks</span></span>  
 <span data-ttu-id="c6239-111">プロセスが停止した場合`Terminate`が呼び出されると、プロセスを続行するかを使用して、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッドをデバッガーは、終了からの確認を受信するよう、 [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)または[icordebugmanagedcallback::exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="c6239-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6239-112">このメソッドは、アプリケーション ドメインによって実装されていません。</span><span class="sxs-lookup"><span data-stu-id="c6239-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="c6239-113">つまり、その実装されていません、<xref:System.AppDomain>レベル。</span><span class="sxs-lookup"><span data-stu-id="c6239-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6239-114">要件</span><span class="sxs-lookup"><span data-stu-id="c6239-114">Requirements</span></span>  
 <span data-ttu-id="c6239-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6239-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6239-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6239-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6239-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6239-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6239-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6239-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6239-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6239-119">See Also</span></span>  
 
