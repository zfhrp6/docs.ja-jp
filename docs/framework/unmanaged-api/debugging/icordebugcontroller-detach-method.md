---
title: ICorDebugController::Detach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cad8b305de580ce7cf4876939b95cc05d0fd11f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="f1130-102">ICorDebugController::Detach メソッド</span><span class="sxs-lookup"><span data-stu-id="f1130-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="f1130-103">プロセスまたはアプリケーション ドメインからデバッガーをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="f1130-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1130-104">構文</span><span class="sxs-lookup"><span data-stu-id="f1130-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f1130-105">コメント</span><span class="sxs-lookup"><span data-stu-id="f1130-105">Remarks</span></span>  
 <span data-ttu-id="f1130-106">プロセスまたはアプリケーション ドメインが通常は、実行を続けますが、"ICorDebugProcess"または"ICorDebugAppDomain"オブジェクトが有効ではなくとさらにコールバックが行われません。</span><span class="sxs-lookup"><span data-stu-id="f1130-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="f1130-107">.NET framework version 2.0 では、アンマネージ デバッグが有効になっている場合は、このメソッドはオペレーティング システムの制限により失敗します。</span><span class="sxs-lookup"><span data-stu-id="f1130-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1130-108">要件</span><span class="sxs-lookup"><span data-stu-id="f1130-108">Requirements</span></span>  
 <span data-ttu-id="f1130-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f1130-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1130-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1130-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1130-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1130-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1130-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1130-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1130-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1130-113">See Also</span></span>  
 
