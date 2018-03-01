---
title: "ICorProfilerInfo::GetFunctionFromToken メソッド"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c90a63f075c392ca3ff02a47190f9c4dfe6aad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="31217-102">ICorProfilerInfo::GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="31217-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="31217-103">関数の ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="31217-103">Gets the ID of a function.</span></span> <span data-ttu-id="31217-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="31217-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="31217-105">使用して、 [icorprofilerinfo 2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="31217-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31217-106">構文</span><span class="sxs-lookup"><span data-stu-id="31217-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="31217-107">コメント</span><span class="sxs-lookup"><span data-stu-id="31217-107">Remarks</span></span>  
 <span data-ttu-id="31217-108">`GetFunctionFromToken`メソッドは、ジェネリック関数またはジェネリック型の関数は機能しません。 は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="31217-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="31217-109">使用して`ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`すべての関数。</span><span class="sxs-lookup"><span data-stu-id="31217-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31217-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="31217-110">Requirements</span></span>  
 <span data-ttu-id="31217-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="31217-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31217-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31217-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31217-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31217-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31217-114">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="31217-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31217-115">参照</span><span class="sxs-lookup"><span data-stu-id="31217-115">See Also</span></span>  
 [<span data-ttu-id="31217-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31217-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
