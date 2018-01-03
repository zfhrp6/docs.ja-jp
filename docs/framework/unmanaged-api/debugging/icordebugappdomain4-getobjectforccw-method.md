---
title: "ICorDebugAppDomain4::GetObjectForCCW メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d459c9ea807114c4f63995ba8fbbb288ea5463b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="0186a-102">ICorDebugAppDomain4::GetObjectForCCW メソッド</span><span class="sxs-lookup"><span data-stu-id="0186a-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="0186a-103">COM 呼び出し可能ラッパー (CCW: COM Callable Wrapper) ポインターからマネージ オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="0186a-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0186a-104">構文</span><span class="sxs-lookup"><span data-stu-id="0186a-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0186a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0186a-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="0186a-106">[in] COM 呼び出し可能ラッパー (CCW) ポインター。</span><span class="sxs-lookup"><span data-stu-id="0186a-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="0186a-107">[out]指定の CCW ポインターに対応するマネージ オブジェクトを表す"ICorDebugValue"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0186a-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0186a-108">コメント</span><span class="sxs-lookup"><span data-stu-id="0186a-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0186a-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="0186a-109">Requirements</span></span>  
 <span data-ttu-id="0186a-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0186a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0186a-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0186a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0186a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0186a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0186a-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0186a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0186a-114">参照</span><span class="sxs-lookup"><span data-stu-id="0186a-114">See Also</span></span>  
 [<span data-ttu-id="0186a-115">ICorDebugAppDomain4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0186a-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="0186a-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0186a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
