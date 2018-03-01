---
title: "ICorDebugController::Detach メソッド"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59fe2c4bfbd91afd263a0ada1eb355aaa8914aa2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="adc70-102">ICorDebugController::Detach メソッド</span><span class="sxs-lookup"><span data-stu-id="adc70-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="adc70-103">プロセスまたはアプリケーション ドメインからデバッガーをデタッチします。</span><span class="sxs-lookup"><span data-stu-id="adc70-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc70-104">構文</span><span class="sxs-lookup"><span data-stu-id="adc70-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="adc70-105">コメント</span><span class="sxs-lookup"><span data-stu-id="adc70-105">Remarks</span></span>  
 <span data-ttu-id="adc70-106">プロセスまたはアプリケーション ドメインが通常は、実行を続けますが、"ICorDebugProcess"または"ICorDebugAppDomain"オブジェクトが有効ではなくとさらにコールバックが行われません。</span><span class="sxs-lookup"><span data-stu-id="adc70-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="adc70-107">.NET framework version 2.0 では、アンマネージ デバッグが有効になっている場合は、このメソッドはオペレーティング システムの制限により失敗します。</span><span class="sxs-lookup"><span data-stu-id="adc70-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adc70-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="adc70-108">Requirements</span></span>  
 <span data-ttu-id="adc70-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="adc70-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc70-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="adc70-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adc70-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adc70-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adc70-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc70-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc70-113">参照</span><span class="sxs-lookup"><span data-stu-id="adc70-113">See Also</span></span>  
 
