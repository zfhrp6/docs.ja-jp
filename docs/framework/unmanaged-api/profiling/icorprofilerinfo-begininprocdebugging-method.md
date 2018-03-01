---
title: "ICorProfilerInfo::BeginInprocDebugging メソッド"
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
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91306bbea7b099f7e9e408f8bf69625f1d7da68e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="ef64a-102">ICorProfilerInfo::BeginInprocDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="ef64a-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="ef64a-103">初期化は、プロセス内のデバッグのサポート。</span><span class="sxs-lookup"><span data-stu-id="ef64a-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="ef64a-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="ef64a-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef64a-105">構文</span><span class="sxs-lookup"><span data-stu-id="ef64a-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef64a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef64a-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="ef64a-107">[in]この値を設定`true`だけ現在のスレッドに対するデバッグのサポートを初期化するために設定`false`すべてのスレッドのデバッグのサポートを初期化します。</span><span class="sxs-lookup"><span data-stu-id="ef64a-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="ef64a-108">[out]デバッグ セッションを識別する戻り値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef64a-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef64a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="ef64a-109">Remarks</span></span>  
 <span data-ttu-id="ef64a-110">CLR デバッグ サービスでは、.NET Framework version 1.0 および 1.1 でインプロセスでデバッグを制限をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ef64a-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="ef64a-111">プロセスのデバッグには、プロファイラーは、デバッグ API の検査部分の使用が有効になります。</span><span class="sxs-lookup"><span data-stu-id="ef64a-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="ef64a-112">ただし、お客様のフィードバックによりプロセスでデバッグがバージョン 2.0、.NET Framework から削除されに沿ってプロファイル API は、機能のセットに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="ef64a-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef64a-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="ef64a-113">Requirements</span></span>  
 <span data-ttu-id="ef64a-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef64a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef64a-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ef64a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef64a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef64a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef64a-117">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="ef64a-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef64a-118">参照</span><span class="sxs-lookup"><span data-stu-id="ef64a-118">See Also</span></span>  
 [<span data-ttu-id="ef64a-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef64a-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
