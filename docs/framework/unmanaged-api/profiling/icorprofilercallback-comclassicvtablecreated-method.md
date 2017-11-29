---
title: "ICorProfilerCallback::COMClassicVTableCreated メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39fa655065c2af10750b1285ef047678874723ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="197bc-102">ICorProfilerCallback::COMClassicVTableCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="197bc-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="197bc-103">指定された IID およびクラスの COM 相互運用機能の vtable が作成されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="197bc-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="197bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="197bc-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="197bc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="197bc-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="197bc-106">[in]Vtable が作成されたクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="197bc-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="197bc-107">[in]クラスによって実装されるインターフェイスの ID。</span><span class="sxs-lookup"><span data-stu-id="197bc-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="197bc-108">場合は、インターフェイスは内部でのみ、この値は NULL にすることがあります。</span><span class="sxs-lookup"><span data-stu-id="197bc-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="197bc-109">[in]Vtable の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="197bc-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="197bc-110">[in]Vtable されているスロットの数。</span><span class="sxs-lookup"><span data-stu-id="197bc-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="197bc-111">コメント</span><span class="sxs-lookup"><span data-stu-id="197bc-111">Remarks</span></span>  
 <span data-ttu-id="197bc-112">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="197bc-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="197bc-113">ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="197bc-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="197bc-114">このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="197bc-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="197bc-115">要件</span><span class="sxs-lookup"><span data-stu-id="197bc-115">Requirements</span></span>  
 <span data-ttu-id="197bc-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="197bc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="197bc-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="197bc-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="197bc-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="197bc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="197bc-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="197bc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197bc-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="197bc-120">See Also</span></span>  
 [<span data-ttu-id="197bc-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="197bc-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="197bc-122">COMClassicVTableDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="197bc-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
