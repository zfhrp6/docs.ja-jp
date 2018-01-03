---
title: "CorDebugStepReason 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStepReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugStepReason
helpviewer_keywords: CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 68c4f9452f8ccc9b4d48ee67755a311f32540247
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="ab58b-102">CorDebugStepReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="ab58b-102">CorDebugStepReason Enumeration</span></span>
<span data-ttu-id="ab58b-103">個々のステップの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="ab58b-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab58b-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab58b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="ab58b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ab58b-105">Members</span></span>  
  
|<span data-ttu-id="ab58b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ab58b-106">Member</span></span>|<span data-ttu-id="ab58b-107">説明</span><span class="sxs-lookup"><span data-stu-id="ab58b-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="ab58b-108">同じ関数内で、ステップ実行が通常は、完了しました。</span><span class="sxs-lookup"><span data-stu-id="ab58b-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="ab58b-109">ステップ実行は継続通常は、関数が返された後。</span><span class="sxs-lookup"><span data-stu-id="ab58b-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="ab58b-110">新しく呼び出された関数の先頭には通常、継続のステップします。</span><span class="sxs-lookup"><span data-stu-id="ab58b-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="ab58b-111">例外が生成され、例外フィルターにコントロールが渡されました。</span><span class="sxs-lookup"><span data-stu-id="ab58b-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="ab58b-112">例外が発生しました、制御、例外ハンドラーに渡されました。</span><span class="sxs-lookup"><span data-stu-id="ab58b-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="ab58b-113">コントロールは、インターセプターに渡されました。</span><span class="sxs-lookup"><span data-stu-id="ab58b-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="ab58b-114">ステップが完了する前に、スレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="ab58b-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab58b-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="ab58b-115">Requirements</span></span>  
 <span data-ttu-id="ab58b-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab58b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab58b-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab58b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab58b-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab58b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab58b-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab58b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab58b-120">参照</span><span class="sxs-lookup"><span data-stu-id="ab58b-120">See Also</span></span>  
 [<span data-ttu-id="ab58b-121">StepComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="ab58b-121">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [<span data-ttu-id="ab58b-122">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="ab58b-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
