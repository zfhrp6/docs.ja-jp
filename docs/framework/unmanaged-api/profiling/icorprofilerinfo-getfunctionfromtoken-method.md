---
title: ICorProfilerInfo::GetFunctionFromToken メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb894e3f52d28ce419ddda90f9fc0ac0e8dce022
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461943"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="9852b-102">ICorProfilerInfo::GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="9852b-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="9852b-103">関数の ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="9852b-103">Gets the ID of a function.</span></span> <span data-ttu-id="9852b-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="9852b-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="9852b-105">使用して、 [icorprofilerinfo 2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="9852b-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9852b-106">構文</span><span class="sxs-lookup"><span data-stu-id="9852b-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="9852b-107">コメント</span><span class="sxs-lookup"><span data-stu-id="9852b-107">Remarks</span></span>  
 <span data-ttu-id="9852b-108">`GetFunctionFromToken`メソッドは、ジェネリック関数またはジェネリック型の関数は機能しません。 は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="9852b-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="9852b-109">使用して`ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`すべての関数。</span><span class="sxs-lookup"><span data-stu-id="9852b-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9852b-110">要件</span><span class="sxs-lookup"><span data-stu-id="9852b-110">Requirements</span></span>  
 <span data-ttu-id="9852b-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9852b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9852b-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9852b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9852b-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9852b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9852b-114">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="9852b-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9852b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9852b-115">See Also</span></span>  
 [<span data-ttu-id="9852b-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9852b-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
