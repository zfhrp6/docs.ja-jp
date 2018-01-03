---
title: ICorDebugObjectEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectEnum
helpviewer_keywords: ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f2610600d102177c80821c78e7d07f8aed1b6de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="d7937-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="d7937-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="d7937-103">ICorDebugEnum メソッドを実装して、相対仮想アドレス (Rva) でオブジェクトの配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="d7937-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7937-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d7937-104">Methods</span></span>  
  
|<span data-ttu-id="d7937-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d7937-105">Method</span></span>|<span data-ttu-id="d7937-106">説明</span><span class="sxs-lookup"><span data-stu-id="d7937-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7937-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="d7937-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="d7937-108">列挙体の現在位置から指定した数のオブジェクトの Rva を取得します。</span><span class="sxs-lookup"><span data-stu-id="d7937-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7937-109">コメント</span><span class="sxs-lookup"><span data-stu-id="d7937-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7937-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d7937-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7937-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="d7937-111">Requirements</span></span>  
 <span data-ttu-id="d7937-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7937-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7937-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7937-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7937-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7937-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7937-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7937-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7937-116">参照</span><span class="sxs-lookup"><span data-stu-id="d7937-116">See Also</span></span>  
 [<span data-ttu-id="d7937-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7937-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
