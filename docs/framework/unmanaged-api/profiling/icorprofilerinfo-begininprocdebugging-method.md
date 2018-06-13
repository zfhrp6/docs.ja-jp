---
title: ICorProfilerInfo::BeginInprocDebugging メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82e798e1a31f771c63e71f2a85f8cbb684b237bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462391"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="b6712-102">ICorProfilerInfo::BeginInprocDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="b6712-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="b6712-103">初期化は、プロセス内のデバッグのサポート。</span><span class="sxs-lookup"><span data-stu-id="b6712-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="b6712-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="b6712-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6712-105">構文</span><span class="sxs-lookup"><span data-stu-id="b6712-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6712-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6712-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="b6712-107">[in]この値を設定`true`だけ現在のスレッドに対するデバッグのサポートを初期化するために設定`false`すべてのスレッドのデバッグのサポートを初期化します。</span><span class="sxs-lookup"><span data-stu-id="b6712-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="b6712-108">[out]デバッグ セッションを識別する戻り値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b6712-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6712-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b6712-109">Remarks</span></span>  
 <span data-ttu-id="b6712-110">CLR デバッグ サービスでは、.NET Framework version 1.0 および 1.1 でインプロセスでデバッグを制限をサポートします。</span><span class="sxs-lookup"><span data-stu-id="b6712-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="b6712-111">プロセスのデバッグには、プロファイラーは、デバッグ API の検査部分の使用が有効になります。</span><span class="sxs-lookup"><span data-stu-id="b6712-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="b6712-112">ただし、お客様のフィードバックによりプロセスでデバッグがバージョン 2.0、.NET Framework から削除されに沿ってプロファイル API は、機能のセットに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="b6712-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6712-113">要件</span><span class="sxs-lookup"><span data-stu-id="b6712-113">Requirements</span></span>  
 <span data-ttu-id="b6712-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6712-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6712-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6712-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6712-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6712-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6712-117">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="b6712-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6712-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6712-118">See Also</span></span>  
 [<span data-ttu-id="b6712-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6712-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
