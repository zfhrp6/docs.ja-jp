---
title: ICorDebugAppDomain4::GetObjectForCCW メソッド
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1089668aa19747f5f694360ebb87098e2df9ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405552"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="5273d-102">ICorDebugAppDomain4::GetObjectForCCW メソッド</span><span class="sxs-lookup"><span data-stu-id="5273d-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="5273d-103">COM 呼び出し可能ラッパー (CCW: COM Callable Wrapper) ポインターからマネージ オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="5273d-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5273d-104">構文</span><span class="sxs-lookup"><span data-stu-id="5273d-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5273d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5273d-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="5273d-106">[in] COM 呼び出し可能ラッパー (CCW) ポインター。</span><span class="sxs-lookup"><span data-stu-id="5273d-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="5273d-107">[out]指定の CCW ポインターに対応するマネージ オブジェクトを表す"ICorDebugValue"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5273d-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5273d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5273d-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5273d-109">要件</span><span class="sxs-lookup"><span data-stu-id="5273d-109">Requirements</span></span>  
 <span data-ttu-id="5273d-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5273d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5273d-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5273d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5273d-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5273d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5273d-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5273d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5273d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5273d-114">See Also</span></span>  
 [<span data-ttu-id="5273d-115">ICorDebugAppDomain4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5273d-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="5273d-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5273d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
