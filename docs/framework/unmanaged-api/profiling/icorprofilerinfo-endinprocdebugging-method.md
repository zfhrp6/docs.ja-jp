---
title: "ICorProfilerInfo::EndInprocDebugging メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.EndInprocDebugging
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a36c557d9ab2fa661808aa2f0be942d11ea9fa61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="87c84-102">ICorProfilerInfo::EndInprocDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="87c84-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="87c84-103">プロセスのデバッグ セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="87c84-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="87c84-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="87c84-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c84-105">構文</span><span class="sxs-lookup"><span data-stu-id="87c84-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87c84-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87c84-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="87c84-107">[in]デバッグ セッションを識別する値。</span><span class="sxs-lookup"><span data-stu-id="87c84-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="87c84-108">この値で受信したものと同じである必要があります、 [icorprofilerinfo::begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="87c84-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87c84-109">コメント</span><span class="sxs-lookup"><span data-stu-id="87c84-109">Remarks</span></span>  
 <span data-ttu-id="87c84-110">呼び出す必要があります[icorprofilerinfo::begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)と`EndInprocDebugging`内で同じコールバック メソッド。</span><span class="sxs-lookup"><span data-stu-id="87c84-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="87c84-111">CLR デバッグ サービスでは、.NET Framework version 1.0 および 1.1 でインプロセスでデバッグを制限をサポートします。</span><span class="sxs-lookup"><span data-stu-id="87c84-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="87c84-112">プロセスのデバッグには、プロファイラーは、デバッグ API の検査部分の使用が有効になります。</span><span class="sxs-lookup"><span data-stu-id="87c84-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="87c84-113">ただし、お客様のフィードバックによりプロセスでデバッグがバージョン 2.0、.NET Framework から削除されに沿ってプロファイル API は、機能のセットに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="87c84-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c84-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="87c84-114">Requirements</span></span>  
 <span data-ttu-id="87c84-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="87c84-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87c84-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87c84-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87c84-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87c84-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87c84-118">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="87c84-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c84-119">参照</span><span class="sxs-lookup"><span data-stu-id="87c84-119">See Also</span></span>  
 [<span data-ttu-id="87c84-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87c84-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
