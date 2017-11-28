---
title: "CorDebugExceptionObjectStackFrame 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionObjectStackFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionObjectStackFrame
helpviewer_keywords: CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf166f606aa2c0e0900356395c36bd6875897e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="c735d-102">CorDebugExceptionObjectStackFrame 構造体</span><span class="sxs-lookup"><span data-stu-id="c735d-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="c735d-103">例外オブジェクトのスタック フレームの情報を表しています。</span><span class="sxs-lookup"><span data-stu-id="c735d-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c735d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c735d-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="c735d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c735d-105">Members</span></span>  
  
|<span data-ttu-id="c735d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c735d-106">Member</span></span>|<span data-ttu-id="c735d-107">説明</span><span class="sxs-lookup"><span data-stu-id="c735d-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="c735d-108">現在のフレーム ICorDebugModule オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c735d-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="c735d-109">現在のフレームの命令ポインター (EIP/RIP) の値。</span><span class="sxs-lookup"><span data-stu-id="c735d-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="c735d-110">現在のフレーム メソッド トークンです。</span><span class="sxs-lookup"><span data-stu-id="c735d-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="c735d-111">フレームが外部の例外の最後のフレームであるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="c735d-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c735d-112">コメント</span><span class="sxs-lookup"><span data-stu-id="c735d-112">Remarks</span></span>  
 <span data-ttu-id="c735d-113">呼び出し元は、使用される ICorDebugModule オブジェクトへのポインターを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c735d-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c735d-114">要件</span><span class="sxs-lookup"><span data-stu-id="c735d-114">Requirements</span></span>  
 <span data-ttu-id="c735d-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c735d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c735d-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c735d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c735d-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c735d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c735d-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c735d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c735d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c735d-119">See Also</span></span>  
 [<span data-ttu-id="c735d-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="c735d-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="c735d-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c735d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
