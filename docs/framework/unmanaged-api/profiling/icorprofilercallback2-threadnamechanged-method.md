---
title: "ICorProfilerCallback2::ThreadNameChanged メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.ThreadNameChanged
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ef0100111aa64aed2df7c63c332b54f026d1e26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="be027-102">ICorProfilerCallback2::ThreadNameChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="be027-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="be027-103">スレッドの名前が変更されたことをコード プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="be027-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be027-104">構文</span><span class="sxs-lookup"><span data-stu-id="be027-104">Syntax</span></span>  
  
```  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be027-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be027-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="be027-106">[in]スレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="be027-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="be027-107">[in]スレッドの新しい名前の長さ。</span><span class="sxs-lookup"><span data-stu-id="be027-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="be027-108">[in]スレッドの新しい名前。</span><span class="sxs-lookup"><span data-stu-id="be027-108">[in] The new name of the thread.</span></span> <span data-ttu-id="be027-109">名前が null で終了していません。</span><span class="sxs-lookup"><span data-stu-id="be027-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be027-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="be027-110">Requirements</span></span>  
 <span data-ttu-id="be027-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="be027-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be027-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be027-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be027-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be027-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be027-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be027-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be027-115">参照</span><span class="sxs-lookup"><span data-stu-id="be027-115">See Also</span></span>  
 [<span data-ttu-id="be027-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be027-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="be027-117">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be027-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
