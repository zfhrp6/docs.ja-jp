---
title: ICorDebugValueBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueBreakpoint
helpviewer_keywords: ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 04ce1827bbc70fc4f1406f802c3a382858b08699
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="f80d4-102">ICorDebugValueBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="f80d4-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="f80d4-103">特定の値へのアクセスを提供する ICorDebugBreakpoint インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="f80d4-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f80d4-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f80d4-104">Methods</span></span>  
  
|<span data-ttu-id="f80d4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f80d4-105">Method</span></span>|<span data-ttu-id="f80d4-106">説明</span><span class="sxs-lookup"><span data-stu-id="f80d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f80d4-107">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="f80d4-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="f80d4-108">ブレークポイントが設定されているオブジェクトの値を表す ICorDebugValue オブジェクトへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="f80d4-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f80d4-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f80d4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f80d4-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f80d4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f80d4-111">要件</span><span class="sxs-lookup"><span data-stu-id="f80d4-111">Requirements</span></span>  
 <span data-ttu-id="f80d4-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f80d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f80d4-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f80d4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f80d4-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f80d4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f80d4-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f80d4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80d4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f80d4-116">See Also</span></span>  
 [<span data-ttu-id="f80d4-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f80d4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
