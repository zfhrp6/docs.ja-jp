---
title: ICorProfilerInfo::GetClassFromObject メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 104dfcaa4120d72f3aa758b66134050f178fef75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453422"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="ded13-102">ICorProfilerInfo::GetClassFromObject メソッド</span><span class="sxs-lookup"><span data-stu-id="ded13-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="ded13-103">取得、`ClassID`指定して、オブジェクトの`ObjectID`です。</span><span class="sxs-lookup"><span data-stu-id="ded13-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded13-104">構文</span><span class="sxs-lookup"><span data-stu-id="ded13-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ded13-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ded13-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="ded13-106">[in]取得する対象のオブジェクトの ID、`ClassID`です。</span><span class="sxs-lookup"><span data-stu-id="ded13-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="ded13-107">[out]返されたへのポインター`ClassID`です。</span><span class="sxs-lookup"><span data-stu-id="ded13-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ded13-108">コメント</span><span class="sxs-lookup"><span data-stu-id="ded13-108">Remarks</span></span>  
 <span data-ttu-id="ded13-109">Null`pClassId`ことを示します`objectId`型がアンロード中が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ded13-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ded13-110">要件</span><span class="sxs-lookup"><span data-stu-id="ded13-110">Requirements</span></span>  
 <span data-ttu-id="ded13-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ded13-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded13-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ded13-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ded13-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ded13-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ded13-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ded13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded13-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ded13-115">See Also</span></span>  
 [<span data-ttu-id="ded13-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ded13-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
