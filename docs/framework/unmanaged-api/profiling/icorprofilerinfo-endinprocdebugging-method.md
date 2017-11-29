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
ms.openlocfilehash: 6e87cf210fb2717379e6bdc0b687028d680fe624
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="fc3e6-102">ICorProfilerInfo::EndInprocDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="fc3e6-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="fc3e6-103">プロセスのデバッグ セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="fc3e6-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="fc3e6-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc3e6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc3e6-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="fc3e6-107">[in]デバッグ セッションを識別する値。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="fc3e6-108">この値で受信したものと同じである必要があります、 [icorprofilerinfo::begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc3e6-109">コメント</span><span class="sxs-lookup"><span data-stu-id="fc3e6-109">Remarks</span></span>  
 <span data-ttu-id="fc3e6-110">呼び出す必要があります[icorprofilerinfo::begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)と`EndInprocDebugging`内で同じコールバック メソッド。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="fc3e6-111">CLR デバッグ サービスでは、.NET Framework version 1.0 および 1.1 でインプロセスでデバッグを制限をサポートします。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="fc3e6-112">プロセスのデバッグには、プロファイラーは、デバッグ API の検査部分の使用が有効になります。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="fc3e6-113">ただし、お客様のフィードバックによりプロセスでデバッグがバージョン 2.0、.NET Framework から削除されに沿ってプロファイル API は、機能のセットに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc3e6-114">要件</span><span class="sxs-lookup"><span data-stu-id="fc3e6-114">Requirements</span></span>  
 <span data-ttu-id="fc3e6-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc3e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc3e6-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc3e6-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc3e6-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc3e6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc3e6-118">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="fc3e6-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3e6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc3e6-119">See Also</span></span>  
 [<span data-ttu-id="fc3e6-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc3e6-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
