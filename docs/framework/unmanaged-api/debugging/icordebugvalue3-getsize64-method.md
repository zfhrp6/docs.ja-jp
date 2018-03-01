---
title: "ICorDebugValue3::GetSize64 メソッド"
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
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4eb0c4691b82bdfaecb97c5969a942c113987c04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="09065-102">ICorDebugValue3::GetSize64 メソッド</span><span class="sxs-lookup"><span data-stu-id="09065-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="09065-103">サイズを取得します (バイト単位) のこの[ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="09065-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09065-104">構文</span><span class="sxs-lookup"><span data-stu-id="09065-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09065-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09065-105">Parameters</span></span>  
 <span data-ttu-id="09065-106">pSize</span><span class="sxs-lookup"><span data-stu-id="09065-106">pSize</span></span>  
 <span data-ttu-id="09065-107">[out]このオブジェクトのバイト単位のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="09065-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09065-108">コメント</span><span class="sxs-lookup"><span data-stu-id="09065-108">Remarks</span></span>  
 <span data-ttu-id="09065-109">この値の型が参照型の場合は、このメソッドは、オブジェクトのサイズではなく、ポインターのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="09065-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="09065-110">`ICorDebugValue3::GetSize`メソッドとは異なります、 [icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)出力パラメーターの型のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="09065-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="09065-111">[ICorDebugValue :: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)では、出力パラメータは`ULONG32`です。 `ICorDebugValue3::GetSize`で、それは`ULONG64`です。</span><span class="sxs-lookup"><span data-stu-id="09065-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="09065-112">これにより、 [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) 2 GB を超える配列のサイズを報告するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="09065-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09065-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="09065-113">Requirements</span></span>  
 <span data-ttu-id="09065-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="09065-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09065-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09065-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09065-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09065-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09065-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09065-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09065-118">参照</span><span class="sxs-lookup"><span data-stu-id="09065-118">See Also</span></span>  
 [<span data-ttu-id="09065-119">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09065-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="09065-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09065-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
