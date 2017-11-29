---
title: "ICorProfilerCallback::COMClassicVTableDestroyed メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebff8297a708b130a0d3983fd75b76c3aeaeceaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="5da0e-102">ICorProfilerCallback::COMClassicVTableDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="5da0e-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="5da0e-103">COM 相互運用機能の vtable が破棄されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5da0e-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5da0e-104">このコールバックは、シャット ダウンに近いに vtable の破壊が発生するので、発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="5da0e-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da0e-105">構文</span><span class="sxs-lookup"><span data-stu-id="5da0e-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5da0e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5da0e-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="5da0e-107">[in]この vtable の作成対象のクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="5da0e-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="5da0e-108">[in]クラスによって実装されるインターフェイスの ID。</span><span class="sxs-lookup"><span data-stu-id="5da0e-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="5da0e-109">場合は、インターフェイスは内部でのみ、この値は NULL にすることがあります。</span><span class="sxs-lookup"><span data-stu-id="5da0e-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="5da0e-110">[in]Vtable の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5da0e-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5da0e-111">コメント</span><span class="sxs-lookup"><span data-stu-id="5da0e-111">Remarks</span></span>  
 <span data-ttu-id="5da0e-112">プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。</span><span class="sxs-lookup"><span data-stu-id="5da0e-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="5da0e-113">ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="5da0e-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="5da0e-114">このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5da0e-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5da0e-115">要件</span><span class="sxs-lookup"><span data-stu-id="5da0e-115">Requirements</span></span>  
 <span data-ttu-id="5da0e-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5da0e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5da0e-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5da0e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5da0e-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5da0e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5da0e-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5da0e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da0e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5da0e-120">See Also</span></span>  
 [<span data-ttu-id="5da0e-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5da0e-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5da0e-122">COMClassicVTableCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="5da0e-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
