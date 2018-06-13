---
title: ICorDebugGenericValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0081f020da673023e2c35f9599e9682215e2c9d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415065"
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="91ee4-102">ICorDebugGenericValue Interface1</span><span class="sxs-lookup"><span data-stu-id="91ee4-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="91ee4-103">すべての値に適用される"ICorDebugValue"のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="91ee4-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="91ee4-104">このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="91ee4-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91ee4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="91ee4-105">Methods</span></span>  
  
|<span data-ttu-id="91ee4-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="91ee4-106">Method</span></span>|<span data-ttu-id="91ee4-107">説明</span><span class="sxs-lookup"><span data-stu-id="91ee4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91ee4-108">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="91ee4-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="91ee4-109">値が指定されたバッファーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="91ee4-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="91ee4-110">SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="91ee4-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="91ee4-111">指定されたバッファーから新しい値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="91ee4-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91ee4-112">コメント</span><span class="sxs-lookup"><span data-stu-id="91ee4-112">Remarks</span></span>  
 <span data-ttu-id="91ee4-113">`ICorDebugGenericValue` 非リモート化可能になっているために、サブ インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="91ee4-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="91ee4-114">参照型の値は、参照の内容ではなく、参照です。</span><span class="sxs-lookup"><span data-stu-id="91ee4-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="91ee4-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="91ee4-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91ee4-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="91ee4-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ee4-117">要件</span><span class="sxs-lookup"><span data-stu-id="91ee4-117">Requirements</span></span>  
 <span data-ttu-id="91ee4-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="91ee4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ee4-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91ee4-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91ee4-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91ee4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91ee4-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ee4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ee4-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="91ee4-122">See Also</span></span>  
    
 [<span data-ttu-id="91ee4-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91ee4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
