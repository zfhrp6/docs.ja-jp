---
title: ICorDebugBoxValue Interface1
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
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 43c4a1d0e8805fc3692aa96668a7f3ea567718f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugboxvalue-interface1"></a><span data-ttu-id="b66d2-102">ICorDebugBoxValue Interface1</span><span class="sxs-lookup"><span data-stu-id="b66d2-102">ICorDebugBoxValue Interface1</span></span>
<span data-ttu-id="b66d2-103">ボックス化された値クラス オブジェクトを表す"ICorDebugHeapValue"のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="b66d2-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b66d2-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b66d2-104">Methods</span></span>  
  
|<span data-ttu-id="b66d2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b66d2-105">Method</span></span>|<span data-ttu-id="b66d2-106">説明</span><span class="sxs-lookup"><span data-stu-id="b66d2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b66d2-107">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="b66d2-107">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-getobject-method.md)|<span data-ttu-id="b66d2-108">ボックス化された"ICorDebugObjectValue"インスタンスへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b66d2-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b66d2-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b66d2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b66d2-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b66d2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b66d2-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="b66d2-111">Requirements</span></span>  
 <span data-ttu-id="b66d2-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b66d2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b66d2-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b66d2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b66d2-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b66d2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b66d2-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b66d2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b66d2-116">参照</span><span class="sxs-lookup"><span data-stu-id="b66d2-116">See Also</span></span>  
 [<span data-ttu-id="b66d2-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b66d2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
