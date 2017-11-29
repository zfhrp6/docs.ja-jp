---
title: "ICorDebugMutableDataTarget::ContinueStatusChanged メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2f4f3890f2cfb2e3b017b8c7d0705d8c8e063957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="bbfaf-102">ICorDebugMutableDataTarget::ContinueStatusChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="bbfaf-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="bbfaf-103">指定のスレッド上にある未処理のデバッグ イベントの継続状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="bbfaf-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfaf-104">構文</span><span class="sxs-lookup"><span data-stu-id="bbfaf-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbfaf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbfaf-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="bbfaf-106">オペレーティング システム定義のスレッド識別子です。</span><span class="sxs-lookup"><span data-stu-id="bbfaf-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="bbfaf-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)要求された継続状態を表す新しい値。</span><span class="sxs-lookup"><span data-stu-id="bbfaf-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbfaf-108">コメント</span><span class="sxs-lookup"><span data-stu-id="bbfaf-108">Remarks</span></span>  
 <span data-ttu-id="bbfaf-109">デバッガーは、通常の方法とは異なることがある方法で現在のデバッグ イベントを処理するように要求する ICorDebug メソッドを呼び出すときに、`ContinueStatusChanged` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bbfaf-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="bbfaf-110">例で、未処理の例外が発生し、デバッガーが例外をキャンセルする操作を要求する場合 (など[icordebugilframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)または`FuncEval`)、この API は、例外があることを要求するために使用取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bbfaf-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfaf-111">要件</span><span class="sxs-lookup"><span data-stu-id="bbfaf-111">Requirements</span></span>  
 <span data-ttu-id="bbfaf-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bbfaf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbfaf-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbfaf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbfaf-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbfaf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbfaf-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbfaf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfaf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbfaf-116">See Also</span></span>  
 [<span data-ttu-id="bbfaf-117">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbfaf-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="bbfaf-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbfaf-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
