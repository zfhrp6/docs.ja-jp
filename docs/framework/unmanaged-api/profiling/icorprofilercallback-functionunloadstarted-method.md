---
title: "ICorProfilerCallback::FunctionUnloadStarted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.FunctionUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: efd08eedf6812a46a46135eaa6f0089257f0a209
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="26df4-102">ICorProfilerCallback::FunctionUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="26df4-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="26df4-103">関数のアンロードをランタイムが開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="26df4-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26df4-104">構文</span><span class="sxs-lookup"><span data-stu-id="26df4-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="26df4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26df4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="26df4-106">[in]モジュールはアンロードされている関数の ID です。</span><span class="sxs-lookup"><span data-stu-id="26df4-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26df4-107">コメント</span><span class="sxs-lookup"><span data-stu-id="26df4-107">Remarks</span></span>  
 <span data-ttu-id="26df4-108">値、`functionId`このメソッドが呼び出し元に返された後にパラメーターが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="26df4-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26df4-109">要件</span><span class="sxs-lookup"><span data-stu-id="26df4-109">Requirements</span></span>  
 <span data-ttu-id="26df4-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="26df4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26df4-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="26df4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26df4-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26df4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26df4-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26df4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26df4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="26df4-114">See Also</span></span>  
 [<span data-ttu-id="26df4-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26df4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
