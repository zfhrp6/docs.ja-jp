---
title: ICorDebugMDA::GetOSThreadId メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20833624b4b853a1a56964e11a25f446c6b39053
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414714"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="37329-102">ICorDebugMDA::GetOSThreadId メソッド</span><span class="sxs-lookup"><span data-stu-id="37329-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="37329-103">識別子を取得します (OS) のオペレーティング システム スレッドによって基になるマネージ デバッグ アシスタント (MDA) が表される[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)を実行します。</span><span class="sxs-lookup"><span data-stu-id="37329-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37329-104">構文</span><span class="sxs-lookup"><span data-stu-id="37329-104">Syntax</span></span>  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37329-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37329-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="37329-106">[out]OS スレッド識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="37329-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37329-107">コメント</span><span class="sxs-lookup"><span data-stu-id="37329-107">Remarks</span></span>  
 <span data-ttu-id="37329-108">OS スレッドは、ネイティブ スレッドで、またはマネージ コードがまだ入力されているマネージ スレッドでの MDA が発生する場合に使用できるように、ICorDebugThread の代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="37329-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37329-109">要件</span><span class="sxs-lookup"><span data-stu-id="37329-109">Requirements</span></span>  
 <span data-ttu-id="37329-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="37329-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37329-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37329-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37329-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37329-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37329-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37329-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37329-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="37329-114">See Also</span></span>  
 [<span data-ttu-id="37329-115">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37329-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="37329-116">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="37329-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
