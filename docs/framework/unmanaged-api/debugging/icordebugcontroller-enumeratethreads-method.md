---
title: "ICorDebugController::EnumerateThreads メソッド"
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
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61d96aa6c8ae4a50c3afbcd84033244208e2444d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="d8d7f-102">ICorDebugController::EnumerateThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d8d7f-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="d8d7f-103">プロセスのアクティブなマネージ スレッドの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d8d7f-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8d7f-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8d7f-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8d7f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8d7f-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="d8d7f-106">[out]プロセスのアクティブなすべてのマネージ スレッドの列挙子を表す"ICorDebugThreadEnum"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d8d7f-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8d7f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="d8d7f-107">Remarks</span></span>  
 <span data-ttu-id="d8d7f-108">スレッドの後にアクティブと見なされます、 [icordebugmanagedcallback::createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)コールバックのディスパッチとする前に、 [icordebugmanagedcallback::exitthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)コールバックがディスパッチされました.</span><span class="sxs-lookup"><span data-stu-id="d8d7f-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="d8d7f-109">マネージ スレッドとは限りませんがないマネージ フレーム、スタックにします。</span><span class="sxs-lookup"><span data-stu-id="d8d7f-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="d8d7f-110">スレッドを前であってもに、列挙することができます、 [icordebugmanagedcallback::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="d8d7f-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="d8d7f-111">列挙は空になります。</span><span class="sxs-lookup"><span data-stu-id="d8d7f-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8d7f-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="d8d7f-112">Requirements</span></span>  
 <span data-ttu-id="d8d7f-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8d7f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8d7f-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8d7f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8d7f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8d7f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8d7f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8d7f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d7f-117">参照</span><span class="sxs-lookup"><span data-stu-id="d8d7f-117">See Also</span></span>  
 
