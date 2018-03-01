---
title: "CorDebugExceptionObjectStackFrame 構造体"
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
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f2d3f0d0c17c0fdf8b772ba38ae97fd8e406be8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="8f1d7-102">CorDebugExceptionObjectStackFrame 構造体</span><span class="sxs-lookup"><span data-stu-id="8f1d7-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="8f1d7-103">例外オブジェクトのスタック フレームの情報を表しています。</span><span class="sxs-lookup"><span data-stu-id="8f1d7-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f1d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="8f1d7-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="8f1d7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="8f1d7-105">Members</span></span>  
  
|<span data-ttu-id="8f1d7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8f1d7-106">Member</span></span>|<span data-ttu-id="8f1d7-107">説明</span><span class="sxs-lookup"><span data-stu-id="8f1d7-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="8f1d7-108">現在のフレーム ICorDebugModule オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8f1d7-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="8f1d7-109">現在のフレームの命令ポインター (EIP/RIP) の値。</span><span class="sxs-lookup"><span data-stu-id="8f1d7-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="8f1d7-110">現在のフレーム メソッド トークンです。</span><span class="sxs-lookup"><span data-stu-id="8f1d7-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="8f1d7-111">フレームが外部の例外の最後のフレームであるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="8f1d7-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f1d7-112">コメント</span><span class="sxs-lookup"><span data-stu-id="8f1d7-112">Remarks</span></span>  
 <span data-ttu-id="8f1d7-113">呼び出し元は、使用される ICorDebugModule オブジェクトへのポインターを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f1d7-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f1d7-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="8f1d7-114">Requirements</span></span>  
 <span data-ttu-id="8f1d7-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8f1d7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f1d7-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f1d7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f1d7-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f1d7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f1d7-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f1d7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f1d7-119">参照</span><span class="sxs-lookup"><span data-stu-id="8f1d7-119">See Also</span></span>  
 [<span data-ttu-id="8f1d7-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="8f1d7-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="8f1d7-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8f1d7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
