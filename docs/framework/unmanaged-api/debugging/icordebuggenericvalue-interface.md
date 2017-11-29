---
title: ICorDebugGenericValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue
helpviewer_keywords: ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61c159e30efb33dca4043e5b5306c9544acd614a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="4725e-102">ICorDebugGenericValue Interface1</span><span class="sxs-lookup"><span data-stu-id="4725e-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="4725e-103">すべての値に適用される"ICorDebugValue"のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="4725e-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="4725e-104">このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4725e-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4725e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4725e-105">Methods</span></span>  
  
|<span data-ttu-id="4725e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="4725e-106">Method</span></span>|<span data-ttu-id="4725e-107">説明</span><span class="sxs-lookup"><span data-stu-id="4725e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4725e-108">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="4725e-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="4725e-109">値が指定されたバッファーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="4725e-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="4725e-110">SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="4725e-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="4725e-111">指定されたバッファーから新しい値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="4725e-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4725e-112">コメント</span><span class="sxs-lookup"><span data-stu-id="4725e-112">Remarks</span></span>  
 <span data-ttu-id="4725e-113">`ICorDebugGenericValue`非リモート化可能になっているために、サブ インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="4725e-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="4725e-114">参照型の値は、参照の内容ではなく、参照です。</span><span class="sxs-lookup"><span data-stu-id="4725e-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="4725e-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4725e-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4725e-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4725e-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4725e-117">要件</span><span class="sxs-lookup"><span data-stu-id="4725e-117">Requirements</span></span>  
 <span data-ttu-id="4725e-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4725e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4725e-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4725e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4725e-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4725e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4725e-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4725e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4725e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4725e-122">See Also</span></span>  
    
 [<span data-ttu-id="4725e-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4725e-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
