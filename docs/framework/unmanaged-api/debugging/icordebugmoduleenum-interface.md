---
title: ICorDebugModuleEnum Interface1
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
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 466eada867dc6c424d4050d732eda67afd100232
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenum-interface1"></a><span data-ttu-id="707b1-102">ICorDebugModuleEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="707b1-102">ICorDebugModuleEnum Interface1</span></span>
<span data-ttu-id="707b1-103">ICorDebugEnum メソッドを実装して、ICorDebugModule 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="707b1-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="707b1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="707b1-104">Methods</span></span>  
  
|<span data-ttu-id="707b1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="707b1-105">Method</span></span>|<span data-ttu-id="707b1-106">説明</span><span class="sxs-lookup"><span data-stu-id="707b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="707b1-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="707b1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="707b1-108">指定した数を取得`ICorDebugModule`列挙体の現在位置からのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="707b1-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="707b1-109">コメント</span><span class="sxs-lookup"><span data-stu-id="707b1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="707b1-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="707b1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="707b1-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="707b1-111">Requirements</span></span>  
 <span data-ttu-id="707b1-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="707b1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="707b1-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="707b1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="707b1-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="707b1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="707b1-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="707b1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707b1-116">参照</span><span class="sxs-lookup"><span data-stu-id="707b1-116">See Also</span></span>  
 [<span data-ttu-id="707b1-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="707b1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
