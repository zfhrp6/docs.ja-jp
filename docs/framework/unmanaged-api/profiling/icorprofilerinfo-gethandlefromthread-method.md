---
title: "ICorProfilerInfo::GetHandleFromThread メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetHandleFromThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be925bbbcc86785feae28353dbc6563974aae2c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="cc9ac-102">ICorProfilerInfo::GetHandleFromThread メソッド</span><span class="sxs-lookup"><span data-stu-id="cc9ac-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="cc9ac-103">Win32 スレッド ハンドルをスレッドの ID を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="cc9ac-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc9ac-104">構文</span><span class="sxs-lookup"><span data-stu-id="cc9ac-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc9ac-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc9ac-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="cc9ac-106">[in]マップするスレッドの ID です。</span><span class="sxs-lookup"><span data-stu-id="cc9ac-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="cc9ac-107">[out]Win32 スレッド ハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cc9ac-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc9ac-108">コメント</span><span class="sxs-lookup"><span data-stu-id="cc9ac-108">Remarks</span></span>  
 <span data-ttu-id="cc9ac-109">プロファイラーは、Win32 を呼び出す必要があります`DuplicateHandle`関数を使用する前に、ハンドル。</span><span class="sxs-lookup"><span data-stu-id="cc9ac-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc9ac-110">要件</span><span class="sxs-lookup"><span data-stu-id="cc9ac-110">Requirements</span></span>  
 <span data-ttu-id="cc9ac-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc9ac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc9ac-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc9ac-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc9ac-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc9ac-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc9ac-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc9ac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9ac-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc9ac-115">See Also</span></span>  
 [<span data-ttu-id="cc9ac-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc9ac-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
