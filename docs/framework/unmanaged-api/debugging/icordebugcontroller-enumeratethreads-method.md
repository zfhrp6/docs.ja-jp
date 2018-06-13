---
title: ICorDebugController::EnumerateThreads メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f8276e2a8fd1bdc546add2ae1ca5d96298186c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412832"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="2f6b2-102">ICorDebugController::EnumerateThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="2f6b2-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="2f6b2-103">プロセスのアクティブなマネージ スレッドの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f6b2-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f6b2-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f6b2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f6b2-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="2f6b2-106">[out]プロセスのアクティブなすべてのマネージ スレッドの列挙子を表す"ICorDebugThreadEnum"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f6b2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="2f6b2-107">Remarks</span></span>  
 <span data-ttu-id="2f6b2-108">スレッドの後にアクティブと見なされます、 [icordebugmanagedcallback::createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)コールバックのディスパッチとする前に、 [icordebugmanagedcallback::exitthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)コールバックがディスパッチされました.</span><span class="sxs-lookup"><span data-stu-id="2f6b2-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="2f6b2-109">マネージ スレッドとは限りませんがないマネージ フレーム、スタックにします。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="2f6b2-110">スレッドを前であってもに、列挙することができます、 [icordebugmanagedcallback::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="2f6b2-111">列挙は空になります。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f6b2-112">要件</span><span class="sxs-lookup"><span data-stu-id="2f6b2-112">Requirements</span></span>  
 <span data-ttu-id="2f6b2-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f6b2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f6b2-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f6b2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f6b2-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f6b2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f6b2-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f6b2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6b2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f6b2-117">See Also</span></span>  
 
