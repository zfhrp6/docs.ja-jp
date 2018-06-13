---
title: ICorDebugComObjectValue::GetCachedInterfacePointers メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef6fb76ca25a1255393b66c52d82cb94df2b48b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411903"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="389b9-102">ICorDebugComObjectValue::GetCachedInterfacePointers メソッド</span><span class="sxs-lookup"><span data-stu-id="389b9-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="389b9-103">現在のランタイム呼び出し可能ラッパー (RCW) 上にキャッシュされた生のインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="389b9-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="389b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="389b9-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="389b9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="389b9-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="389b9-106">[in]メソッドはのみ返すかどうかを示す値[!INCLUDE[wrt](../../../../includes/wrt-md.md)]インターフェイス (`IInspectable`インターフェイス) またはランタイム呼び出し可能ラッパー (RCW) によってキャッシュされているすべての COM インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="389b9-106">[in] A value that indicates whether the method will return only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="389b9-107">[in]アドレスを持つを取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="389b9-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="389b9-108">[out]数へのポインター`CORDB_ADDRESS`で実際に返される値`ptrs`です。</span><span class="sxs-lookup"><span data-stu-id="389b9-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="389b9-109">配列の開始アドレスへのポインター`CORDB_ADDRESS`のアドレスを格納した値は、インターフェイス オブジェクトをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="389b9-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="389b9-110">コメント</span><span class="sxs-lookup"><span data-stu-id="389b9-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="389b9-111">要件</span><span class="sxs-lookup"><span data-stu-id="389b9-111">Requirements</span></span>  
 <span data-ttu-id="389b9-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="389b9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="389b9-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="389b9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="389b9-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="389b9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="389b9-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="389b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="389b9-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="389b9-116">See Also</span></span>  
 [<span data-ttu-id="389b9-117">ICorDebugComObjectValue のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="389b9-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="389b9-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="389b9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
