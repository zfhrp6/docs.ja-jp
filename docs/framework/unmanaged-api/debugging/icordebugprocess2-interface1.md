---
title: ICorDebugProcess2 Interface1
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
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 80f6c35ba2ef2ec74293d0f025ddf20254f504a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2-interface1"></a><span data-ttu-id="d19ef-102">ICorDebugProcess2 Interface1</span><span class="sxs-lookup"><span data-stu-id="d19ef-102">ICorDebugProcess2 Interface1</span></span>
<span data-ttu-id="d19ef-103">マネージ コードを実行するプロセスを表す ICorDebugProcess インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="d19ef-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d19ef-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-104">Methods</span></span>  
  
|<span data-ttu-id="d19ef-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-105">Method</span></span>|<span data-ttu-id="d19ef-106">説明</span><span class="sxs-lookup"><span data-stu-id="d19ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d19ef-107">ClearUnmanagedBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="d19ef-108">指定したオフセットを以前の呼び出しによって設定されたブレークポイントを削除`ICorDebugProcess2::SetUnmanagedBreakpoint`です。</span><span class="sxs-lookup"><span data-stu-id="d19ef-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="d19ef-109">GetDesiredNGENCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="d19ef-110">これによって参照されているプロセスにイメージの読み込みに共通言語ランタイム (CLR) に設定する必要がありますフラグを取得`ICorDebugProcess2`です。</span><span class="sxs-lookup"><span data-stu-id="d19ef-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="d19ef-111">GetReferenceValueFromGCHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="d19ef-112">ガベージ コレクション ハンドルを持つ指定したマネージ オブジェクトへの参照へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d19ef-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="d19ef-113">GetThreadForTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="d19ef-114">指定した識別子を持つタスクを実行する基になるスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="d19ef-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="d19ef-115">GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="d19ef-116">基になる、デバッグ中のプロセスが実行されている CLR のバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="d19ef-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="d19ef-117">SetDesiredNGENCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="d19ef-118">・ イン タイム (JIT) コンパイラがデバッグ中のプロセスにイメージを読み込むを必要とされるフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="d19ef-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="d19ef-119">SetUnmanagedBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="d19ef-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="d19ef-120">ネイティブ イメージを指定したオフセット位置には、アンマネージのブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="d19ef-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d19ef-121">コメント</span><span class="sxs-lookup"><span data-stu-id="d19ef-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d19ef-122">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d19ef-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d19ef-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="d19ef-123">Requirements</span></span>  
 <span data-ttu-id="d19ef-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d19ef-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d19ef-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d19ef-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d19ef-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d19ef-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d19ef-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d19ef-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d19ef-128">参照</span><span class="sxs-lookup"><span data-stu-id="d19ef-128">See Also</span></span>  
 [<span data-ttu-id="d19ef-129">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d19ef-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
