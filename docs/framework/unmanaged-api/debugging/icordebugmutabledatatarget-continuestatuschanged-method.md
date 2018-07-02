---
title: ICorDebugMutableDataTarget::ContinueStatusChanged メソッド
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d2560aa484c6965047b2fdaf2c539b8ab675bc8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207704"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="c8b1d-102">ICorDebugMutableDataTarget::ContinueStatusChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="c8b1d-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="c8b1d-103">指定のスレッド上にある未処理のデバッグ イベントの継続状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="c8b1d-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b1d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8b1d-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8b1d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8b1d-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="c8b1d-106">オペレーティング システム定義のスレッド識別子です。</span><span class="sxs-lookup"><span data-stu-id="c8b1d-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="c8b1d-107">新たに要求された継続状態を表す [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="c8b1d-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8b1d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="c8b1d-108">Remarks</span></span>  
 <span data-ttu-id="c8b1d-109">デバッガーは、通常の方法とは異なることがある方法で現在のデバッグ イベントを処理するように要求する ICorDebug メソッドを呼び出すときに、`ContinueStatusChanged` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c8b1d-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="c8b1d-110">たとえば、未処理の例外が発生して、デバッガーが例外をキャンセルする操作 ([ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) または `FuncEval` など) を要求する場合、この API は例外のキャンセルを要求するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8b1d-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b1d-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="c8b1d-111">Requirements</span></span>  
 <span data-ttu-id="c8b1d-112">**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b1d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8b1d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8b1d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8b1d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8b1d-115">**.NET Framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b1d-116">参照</span><span class="sxs-lookup"><span data-stu-id="c8b1d-116">See Also</span></span>  
 [<span data-ttu-id="c8b1d-117">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8b1d-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="c8b1d-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8b1d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
