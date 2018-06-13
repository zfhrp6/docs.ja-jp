---
title: ICorProfilerInfo::GetFunctionFromIP メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fba01c1dfdea83b2580f45b7dbcef91fb7b73fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452905"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="3ce58-102">ICorProfilerInfo::GetFunctionFromIP メソッド</span><span class="sxs-lookup"><span data-stu-id="3ce58-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="3ce58-103">マネージ コードの命令ポインターのマップ、`FunctionID`です。</span><span class="sxs-lookup"><span data-stu-id="3ce58-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce58-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ce58-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ce58-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3ce58-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="3ce58-106">[in]マネージ コードで命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="3ce58-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="3ce58-107">[out]返された関数の id。</span><span class="sxs-lookup"><span data-stu-id="3ce58-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ce58-108">要件</span><span class="sxs-lookup"><span data-stu-id="3ce58-108">Requirements</span></span>  
 <span data-ttu-id="3ce58-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3ce58-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ce58-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ce58-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ce58-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ce58-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ce58-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ce58-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce58-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ce58-113">See Also</span></span>  
 [<span data-ttu-id="3ce58-114">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ce58-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
