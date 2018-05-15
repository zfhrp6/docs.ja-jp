---
title: ICorProfilerCallback2::ThreadNameChanged メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6bf11d71b90f11a5d9a3844ed59a8574b7b76699
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="839bb-102">ICorProfilerCallback2::ThreadNameChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="839bb-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="839bb-103">スレッドの名前が変更されたことをコード プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="839bb-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="839bb-104">Syntax</span></span>  
  
```  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="839bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="839bb-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="839bb-106">[in]スレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="839bb-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="839bb-107">[in]スレッドの新しい名前の長さ。</span><span class="sxs-lookup"><span data-stu-id="839bb-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="839bb-108">[in]スレッドの新しい名前。</span><span class="sxs-lookup"><span data-stu-id="839bb-108">[in] The new name of the thread.</span></span> <span data-ttu-id="839bb-109">名前が null で終了していません。</span><span class="sxs-lookup"><span data-stu-id="839bb-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="839bb-110">要件</span><span class="sxs-lookup"><span data-stu-id="839bb-110">Requirements</span></span>  
 <span data-ttu-id="839bb-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="839bb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="839bb-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="839bb-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="839bb-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="839bb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="839bb-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="839bb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839bb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="839bb-115">See Also</span></span>  
 [<span data-ttu-id="839bb-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="839bb-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="839bb-117">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="839bb-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
