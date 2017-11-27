---
title: "ICorDebugValue3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue3
helpviewer_keywords: ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3948a4c404036235767f8de6747966709b75bc4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="23c43-102">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23c43-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="23c43-103">2 GB よりも大きな配列をサポートする"ICorDebugValue"および"ICorDebugValue2"インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="23c43-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23c43-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="23c43-104">Methods</span></span>  
  
|<span data-ttu-id="23c43-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="23c43-105">Method</span></span>|<span data-ttu-id="23c43-106">説明</span><span class="sxs-lookup"><span data-stu-id="23c43-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23c43-107">GetSize64 メソッド</span><span class="sxs-lookup"><span data-stu-id="23c43-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="23c43-108">サイズを取得します (バイト単位) のこの`ICorDebugValue3`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="23c43-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23c43-109">コメント</span><span class="sxs-lookup"><span data-stu-id="23c43-109">Remarks</span></span>  
 <span data-ttu-id="23c43-110">[Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)メソッドは、2,147, 483,647 バイトを 0 からオブジェクトのサイズの範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="23c43-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="23c43-111">[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]配列のサイズが 2 GB を超えることができます。</span><span class="sxs-lookup"><span data-stu-id="23c43-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="23c43-112">`ICorDebugValue3`インターフェイスでは、これらの配列のサイズを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="23c43-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23c43-113">要件</span><span class="sxs-lookup"><span data-stu-id="23c43-113">Requirements</span></span>  
 <span data-ttu-id="23c43-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="23c43-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23c43-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23c43-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23c43-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23c43-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23c43-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23c43-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c43-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="23c43-118">See Also</span></span>  
    
    
 [<span data-ttu-id="23c43-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="23c43-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="23c43-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="23c43-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
