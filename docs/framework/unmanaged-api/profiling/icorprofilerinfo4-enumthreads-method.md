---
title: "ICorProfilerInfo4::EnumThreads メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumThreads
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 20022a3b7353c0e43aaa44e368c06cd79906956e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="00a94-102">ICorProfilerInfo4::EnumThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="00a94-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="00a94-103">プロファイリングされたプロセスのすべてのマネージ スレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="00a94-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a94-104">構文</span><span class="sxs-lookup"><span data-stu-id="00a94-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00a94-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00a94-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="00a94-106">[out]ポインター、 [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="00a94-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00a94-107">コメント</span><span class="sxs-lookup"><span data-stu-id="00a94-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00a94-108">要件</span><span class="sxs-lookup"><span data-stu-id="00a94-108">Requirements</span></span>  
 <span data-ttu-id="00a94-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="00a94-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00a94-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00a94-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00a94-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00a94-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00a94-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00a94-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a94-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="00a94-113">See Also</span></span>  
 [<span data-ttu-id="00a94-114">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00a94-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="00a94-115">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00a94-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="00a94-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="00a94-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="00a94-117">プロファイル</span><span class="sxs-lookup"><span data-stu-id="00a94-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
