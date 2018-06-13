---
title: ICorDebugILCode インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 51c4de0c-3813-4142-be25-a85bb84efb90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bac5578caaf5682c12509b41da77b3d7cca76312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415234"
---
# <a name="icordebugilcode-interface"></a><span data-ttu-id="3dd5c-102">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dd5c-102">ICorDebugILCode Interface</span></span>
<span data-ttu-id="3dd5c-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="3dd5c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3dd5c-104">中間言語 (IL) コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="3dd5c-104">Represents a segment of intermediate language (IL) code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3dd5c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3dd5c-105">Methods</span></span>  
  
|<span data-ttu-id="3dd5c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3dd5c-106">Method</span></span>|<span data-ttu-id="3dd5c-107">説明</span><span class="sxs-lookup"><span data-stu-id="3dd5c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3dd5c-108">GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="3dd5c-108">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)|<span data-ttu-id="3dd5c-109">この IL のために定義された例外処理 (EH) 句のリストへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="3dd5c-109">Returns a pointer to a list of exception handling (EH) clauses that are defined for this IL.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3dd5c-110">要件</span><span class="sxs-lookup"><span data-stu-id="3dd5c-110">Requirements</span></span>  
 <span data-ttu-id="3dd5c-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3dd5c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd5c-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dd5c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dd5c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dd5c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dd5c-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd5c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd5c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dd5c-115">See Also</span></span>  
 [<span data-ttu-id="3dd5c-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dd5c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3dd5c-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3dd5c-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
