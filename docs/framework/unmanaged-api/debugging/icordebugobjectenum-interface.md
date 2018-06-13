---
title: ICorDebugObjectEnum Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3674643d5590c320bddd5a0e6f1f95814e07ecf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420205"
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="71b7c-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="71b7c-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="71b7c-103">ICorDebugEnum メソッドを実装して、相対仮想アドレス (Rva) でオブジェクトの配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="71b7c-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71b7c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="71b7c-104">Methods</span></span>  
  
|<span data-ttu-id="71b7c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="71b7c-105">Method</span></span>|<span data-ttu-id="71b7c-106">説明</span><span class="sxs-lookup"><span data-stu-id="71b7c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71b7c-107">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="71b7c-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="71b7c-108">列挙体の現在位置から指定した数のオブジェクトの Rva を取得します。</span><span class="sxs-lookup"><span data-stu-id="71b7c-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71b7c-109">コメント</span><span class="sxs-lookup"><span data-stu-id="71b7c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71b7c-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="71b7c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71b7c-111">要件</span><span class="sxs-lookup"><span data-stu-id="71b7c-111">Requirements</span></span>  
 <span data-ttu-id="71b7c-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="71b7c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71b7c-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71b7c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71b7c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71b7c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71b7c-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71b7c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b7c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="71b7c-116">See Also</span></span>  
 [<span data-ttu-id="71b7c-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71b7c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
