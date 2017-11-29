---
title: "ICorDebugMutableDataTarget インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef1c0b7a56f6bd1f7e87650b72dfe8b1411ef7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="58e42-102">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58e42-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="58e42-103">拡張、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)変更可能なデータ ターゲットをサポートするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="58e42-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58e42-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="58e42-104">Methods</span></span>  
  
|<span data-ttu-id="58e42-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="58e42-105">Method</span></span>|<span data-ttu-id="58e42-106">説明</span><span class="sxs-lookup"><span data-stu-id="58e42-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58e42-107">ContinueStatusChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="58e42-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="58e42-108">指定のスレッド上にある未処理のデバッグ イベントの継続状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="58e42-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="58e42-109">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="58e42-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="58e42-110">スレッドのコンテキスト (レジスタの値) を設定します。</span><span class="sxs-lookup"><span data-stu-id="58e42-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="58e42-111">WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="58e42-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="58e42-112">ターゲット プロセスのアドレス空間にメモリを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="58e42-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58e42-113">コメント</span><span class="sxs-lookup"><span data-stu-id="58e42-113">Remarks</span></span>  
 <span data-ttu-id="58e42-114">この拡張機能、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)デバッグ ツール (たとえば、ライブ侵デバッグを実行する場合など) ターゲット プロセスを変更することによってインターフェイスを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="58e42-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="58e42-115">これらのメソッドすべては省略可能です。つまり、このインターフェイスを実装しない場合や、これらのメソッドに対する呼び出しに失敗する場合にも、コア検査に基づくデバッグ機能は失われません。</span><span class="sxs-lookup"><span data-stu-id="58e42-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="58e42-116">これらのメソッドからの失敗 `HRESULT` すべては、ICorDebug メソッドからの `HRESULT` として伝達されます。</span><span class="sxs-lookup"><span data-stu-id="58e42-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="58e42-117">1 回の ICorDebug メソッド呼び出しによって複数の変更が行われる可能性があること、および関連する変更をトランザクションごとに適用するメカニズムがないこと (すべてに適用するか、まったく適用しないかのどちらか) に注意してください。</span><span class="sxs-lookup"><span data-stu-id="58e42-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="58e42-118">つまり、(同じ ICorDebug 呼び出しの) 他のユーザーが正常に完了した後に変更を失敗すると、ターゲット プロセスは一貫性のない状態のままになり、デバッグが信頼性に欠ける結果になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="58e42-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58e42-119">要件</span><span class="sxs-lookup"><span data-stu-id="58e42-119">Requirements</span></span>  
 <span data-ttu-id="58e42-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="58e42-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58e42-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58e42-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58e42-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58e42-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58e42-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58e42-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e42-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="58e42-124">See Also</span></span>  
 [<span data-ttu-id="58e42-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="58e42-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="58e42-126">デバッグ</span><span class="sxs-lookup"><span data-stu-id="58e42-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
