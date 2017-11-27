---
title: "ICorDebugILCode インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILCode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 51c4de0c-3813-4142-be25-a85bb84efb90
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 22be32839c5a083502a4cf0507269b3aae0619c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode-interface"></a><span data-ttu-id="b78b1-102">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b78b1-102">ICorDebugILCode Interface</span></span>
<span data-ttu-id="b78b1-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="b78b1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b78b1-104">中間言語 (IL) コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="b78b1-104">Represents a segment of intermediate language (IL) code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b78b1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b78b1-105">Methods</span></span>  
  
|<span data-ttu-id="b78b1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b78b1-106">Method</span></span>|<span data-ttu-id="b78b1-107">説明</span><span class="sxs-lookup"><span data-stu-id="b78b1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b78b1-108">GetEHClauses メソッド</span><span class="sxs-lookup"><span data-stu-id="b78b1-108">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)|<span data-ttu-id="b78b1-109">この IL のために定義された例外処理 (EH) 句のリストへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="b78b1-109">Returns a pointer to a list of exception handling (EH) clauses that are defined for this IL.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b78b1-110">要件</span><span class="sxs-lookup"><span data-stu-id="b78b1-110">Requirements</span></span>  
 <span data-ttu-id="b78b1-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b78b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b78b1-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b78b1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b78b1-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b78b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b78b1-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b78b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b78b1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b78b1-115">See Also</span></span>  
 [<span data-ttu-id="b78b1-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b78b1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b78b1-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b78b1-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
