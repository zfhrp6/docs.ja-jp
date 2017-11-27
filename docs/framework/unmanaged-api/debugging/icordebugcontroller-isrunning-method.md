---
title: "ICorDebugController::IsRunning メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.IsRunning
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0cfb2c0fe3c2ebf9473afc4f1a93f50e8fe437f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="469a0-102">ICorDebugController::IsRunning メソッド</span><span class="sxs-lookup"><span data-stu-id="469a0-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="469a0-103">プロセス内のスレッドが自由に実行中かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="469a0-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="469a0-104">構文</span><span class="sxs-lookup"><span data-stu-id="469a0-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="469a0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="469a0-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="469a0-106">[out]ある値へのポインター`true`自由に、それ以外のプロセス内のスレッドを実行している場合`false`です。</span><span class="sxs-lookup"><span data-stu-id="469a0-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="469a0-107">要件</span><span class="sxs-lookup"><span data-stu-id="469a0-107">Requirements</span></span>  
 <span data-ttu-id="469a0-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="469a0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="469a0-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="469a0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="469a0-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="469a0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="469a0-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="469a0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469a0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="469a0-112">See Also</span></span>  
 
