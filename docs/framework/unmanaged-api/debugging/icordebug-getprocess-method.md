---
title: ICorDebug::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc095b2c9f546e8b75d4330024c8c593f7ada8b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="eb512-102">ICorDebug::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="eb512-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="eb512-103">指定されたプロセスの"ICorDebugProcess"のインスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="eb512-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb512-104">構文</span><span class="sxs-lookup"><span data-stu-id="eb512-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb512-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb512-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="eb512-106">[in]プロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="eb512-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="eb512-107">[out]アドレスへのポインター、`ICorDebugProcess`指定されたプロセスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="eb512-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb512-108">要件</span><span class="sxs-lookup"><span data-stu-id="eb512-108">Requirements</span></span>  
 <span data-ttu-id="eb512-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb512-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb512-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb512-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb512-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb512-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb512-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb512-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb512-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb512-113">See Also</span></span>  
 [<span data-ttu-id="eb512-114">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb512-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
