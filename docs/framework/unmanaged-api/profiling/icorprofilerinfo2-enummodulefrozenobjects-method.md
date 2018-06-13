---
title: ICorProfilerInfo2::EnumModuleFrozenObjects メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77b07dae5b53db58b3628f677be1714e66ac18ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455258"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="ffced-102">ICorProfilerInfo2::EnumModuleFrozenObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="ffced-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="ffced-103">指定されたモジュール内の固定オブジェクト経由の反復処理する列挙子を取得します。このメソッドは今後使用しません。</span><span class="sxs-lookup"><span data-stu-id="ffced-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffced-104">構文</span><span class="sxs-lookup"><span data-stu-id="ffced-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffced-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ffced-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="ffced-106">[in]列挙される固定されたオブジェクトを含むモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="ffced-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="ffced-107">[out]アドレスへのポインター、 [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)インターフェイスで、固定されたオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="ffced-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffced-108">要件</span><span class="sxs-lookup"><span data-stu-id="ffced-108">Requirements</span></span>  
 <span data-ttu-id="ffced-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ffced-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffced-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ffced-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ffced-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffced-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffced-112">**.NET framework のバージョン:** 3.5、3.0 SP1、3.0、2.0 SP1、2.0</span><span class="sxs-lookup"><span data-stu-id="ffced-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffced-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffced-113">See Also</span></span>  
 [<span data-ttu-id="ffced-114">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffced-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="ffced-115">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffced-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
