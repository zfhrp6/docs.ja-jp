---
title: "ICorDebugController::Terminate メソッド"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e7647df7a67d8357e72f8f41b0b3f586675aaac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="46783-102">ICorDebugController::Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="46783-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="46783-103">指定した終了コードを使用して、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="46783-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46783-104">このメソッドは、Win32 のラッパー`TerminateProcess`関数。</span><span class="sxs-lookup"><span data-stu-id="46783-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="46783-105">したがって、 `Terminate` 、同じ終了コードを使用する Win32`TerminateProcess`関数では使用します。</span><span class="sxs-lookup"><span data-stu-id="46783-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46783-106">構文</span><span class="sxs-lookup"><span data-stu-id="46783-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46783-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="46783-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="46783-108">[in]終了コードを示す数値。</span><span class="sxs-lookup"><span data-stu-id="46783-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="46783-109">有効な数値の値は、Winbase.h で定義されます。</span><span class="sxs-lookup"><span data-stu-id="46783-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46783-110">コメント</span><span class="sxs-lookup"><span data-stu-id="46783-110">Remarks</span></span>  
 <span data-ttu-id="46783-111">プロセスが停止した場合`Terminate`が呼び出されると、プロセスを続行するかを使用して、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッドをデバッガーは、終了からの確認を受信するよう、 [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)または[icordebugmanagedcallback::exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="46783-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46783-112">このメソッドは、アプリケーション ドメインによって実装されていません。</span><span class="sxs-lookup"><span data-stu-id="46783-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="46783-113">つまり、その実装されていません、<xref:System.AppDomain>レベル。</span><span class="sxs-lookup"><span data-stu-id="46783-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46783-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="46783-114">Requirements</span></span>  
 <span data-ttu-id="46783-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="46783-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46783-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46783-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46783-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46783-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46783-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46783-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46783-119">参照</span><span class="sxs-lookup"><span data-stu-id="46783-119">See Also</span></span>  
 
