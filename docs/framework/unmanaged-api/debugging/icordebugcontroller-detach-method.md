---
title: "ICorDebugController::Detach メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Detach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d8c1df2fd2aa52f9f5e90a27d42f6568686e908
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="69d18-102">ICorDebugController::Detach メソッド</span><span class="sxs-lookup"><span data-stu-id="69d18-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="69d18-103">プロセスまたはアプリケーション ドメインからデバッガーをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="69d18-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69d18-104">構文</span><span class="sxs-lookup"><span data-stu-id="69d18-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="69d18-105">コメント</span><span class="sxs-lookup"><span data-stu-id="69d18-105">Remarks</span></span>  
 <span data-ttu-id="69d18-106">プロセスまたはアプリケーション ドメインが通常は、実行を続けますが、"ICorDebugProcess"または"ICorDebugAppDomain"オブジェクトが有効ではなくとさらにコールバックが行われません。</span><span class="sxs-lookup"><span data-stu-id="69d18-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="69d18-107">.NET framework version 2.0 では、アンマネージ デバッグが有効になっている場合は、このメソッドはオペレーティング システムの制限により失敗します。</span><span class="sxs-lookup"><span data-stu-id="69d18-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69d18-108">要件</span><span class="sxs-lookup"><span data-stu-id="69d18-108">Requirements</span></span>  
 <span data-ttu-id="69d18-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="69d18-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69d18-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69d18-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69d18-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69d18-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69d18-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69d18-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d18-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="69d18-113">See Also</span></span>  
 
