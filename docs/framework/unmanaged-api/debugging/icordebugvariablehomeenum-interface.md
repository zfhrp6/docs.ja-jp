---
title: "ICorDebugVariableHomeEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a33420d50a964479c74a59bf5b7cc0da320aee04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="700b7-102">ICorDebugVariableHomeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="700b7-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="700b7-103">ローカル変数と関数の引数、列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="700b7-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="700b7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="700b7-104">Methods</span></span>  
  
|<span data-ttu-id="700b7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="700b7-105">Method</span></span>|<span data-ttu-id="700b7-106">説明</span><span class="sxs-lookup"><span data-stu-id="700b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="700b7-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="700b7-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="700b7-108">指定した数を取得[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)ローカル変数と関数の引数に関する情報を格納するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="700b7-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="700b7-109">コメント</span><span class="sxs-lookup"><span data-stu-id="700b7-109">Remarks</span></span>  
 <span data-ttu-id="700b7-110">`ICorDebugVariableHomeEnum`インターフェイスは ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="700b7-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="700b7-111">`ICorDebugVariableHomeEnum`インスタンスが格納されます[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)を呼び出してインスタンス、 [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="700b7-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="700b7-112">各[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)コレクション内のインスタンスは、ローカル変数または関数の引数を表します。</span><span class="sxs-lookup"><span data-stu-id="700b7-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="700b7-113">[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)呼び出すことによって、コレクション内のオブジェクトを列挙することができます、 [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="700b7-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="700b7-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="700b7-114">Requirements</span></span>  
 <span data-ttu-id="700b7-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="700b7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="700b7-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="700b7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="700b7-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="700b7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="700b7-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="700b7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700b7-119">参照</span><span class="sxs-lookup"><span data-stu-id="700b7-119">See Also</span></span>  
 [<span data-ttu-id="700b7-120">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="700b7-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="700b7-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="700b7-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
