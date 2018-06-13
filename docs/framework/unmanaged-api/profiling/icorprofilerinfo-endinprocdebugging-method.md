---
title: ICorProfilerInfo::EndInprocDebugging メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbf7e2e7de54b065f25f3a1873d760ab5051cc91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452612"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="a7b4e-102">ICorProfilerInfo::EndInprocDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="a7b4e-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="a7b4e-103">プロセスのデバッグ セッションを終了します。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="a7b4e-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b4e-105">構文</span><span class="sxs-lookup"><span data-stu-id="a7b4e-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7b4e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a7b4e-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="a7b4e-107">[in]デバッグ セッションを識別する値。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="a7b4e-108">この値で受信したものと同じである必要があります、 [icorprofilerinfo::begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7b4e-109">コメント</span><span class="sxs-lookup"><span data-stu-id="a7b4e-109">Remarks</span></span>  
 <span data-ttu-id="a7b4e-110">呼び出す必要があります[icorprofilerinfo::begininprocdebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)と`EndInprocDebugging`内で同じコールバック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="a7b4e-111">CLR デバッグ サービスでは、.NET Framework version 1.0 および 1.1 でインプロセスでデバッグを制限をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="a7b4e-112">プロセスのデバッグには、プロファイラーは、デバッグ API の検査部分の使用が有効になります。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="a7b4e-113">ただし、お客様のフィードバックによりプロセスでデバッグがバージョン 2.0、.NET Framework から削除されに沿ってプロファイル API は、機能のセットに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b4e-114">要件</span><span class="sxs-lookup"><span data-stu-id="a7b4e-114">Requirements</span></span>  
 <span data-ttu-id="a7b4e-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7b4e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b4e-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a7b4e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7b4e-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7b4e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7b4e-118">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="a7b4e-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b4e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7b4e-119">See Also</span></span>  
 [<span data-ttu-id="a7b4e-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7b4e-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
