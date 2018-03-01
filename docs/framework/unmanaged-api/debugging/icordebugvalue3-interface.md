---
title: "ICorDebugValue3 インターフェイス"
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
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6a470113dc54876937850294f6d99fc15a2cf98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="62a1c-102">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62a1c-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="62a1c-103">2 GB よりも大きな配列をサポートする"ICorDebugValue"および"ICorDebugValue2"インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="62a1c-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="62a1c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="62a1c-104">Methods</span></span>  
  
|<span data-ttu-id="62a1c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="62a1c-105">Method</span></span>|<span data-ttu-id="62a1c-106">説明</span><span class="sxs-lookup"><span data-stu-id="62a1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="62a1c-107">GetSize64 メソッド</span><span class="sxs-lookup"><span data-stu-id="62a1c-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="62a1c-108">サイズを取得します (バイト単位) のこの`ICorDebugValue3`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="62a1c-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62a1c-109">コメント</span><span class="sxs-lookup"><span data-stu-id="62a1c-109">Remarks</span></span>  
 <span data-ttu-id="62a1c-110">[Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)メソッドは、2,147, 483,647 バイトを 0 からオブジェクトのサイズの範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="62a1c-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="62a1c-111">[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]配列のサイズが 2 GB を超えることができます。</span><span class="sxs-lookup"><span data-stu-id="62a1c-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="62a1c-112">`ICorDebugValue3`インターフェイスでは、これらの配列のサイズを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="62a1c-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62a1c-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="62a1c-113">Requirements</span></span>  
 <span data-ttu-id="62a1c-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="62a1c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62a1c-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62a1c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62a1c-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62a1c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62a1c-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62a1c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62a1c-118">参照</span><span class="sxs-lookup"><span data-stu-id="62a1c-118">See Also</span></span>  
    
    
 [<span data-ttu-id="62a1c-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62a1c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="62a1c-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="62a1c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
