---
title: "ICorDebugCode4 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugCode4
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode4
helpviewer_keywords: ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bddbdb0986392bf1d9664e351bcc654ffa526257
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="f9aed-102">ICorDebugCode4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9aed-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="f9aed-103">ローカル変数と関数の引数を列挙するデバッガーを有効にするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9aed-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9aed-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f9aed-104">Methods</span></span>  
  
|<span data-ttu-id="f9aed-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f9aed-105">Method</span></span>|<span data-ttu-id="f9aed-106">説明</span><span class="sxs-lookup"><span data-stu-id="f9aed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9aed-107">EnumerateVariableHomes メソッド</span><span class="sxs-lookup"><span data-stu-id="f9aed-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="f9aed-108">ローカル変数と引数を関数内の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f9aed-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9aed-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f9aed-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9aed-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f9aed-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9aed-111">要件</span><span class="sxs-lookup"><span data-stu-id="f9aed-111">Requirements</span></span>  
 <span data-ttu-id="f9aed-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9aed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9aed-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9aed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9aed-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9aed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9aed-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9aed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9aed-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9aed-116">See Also</span></span>  
    
    
 [<span data-ttu-id="f9aed-117">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9aed-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="f9aed-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9aed-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
