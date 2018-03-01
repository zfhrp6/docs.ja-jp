---
title: "ICorProfilerInfo::GetClassFromToken メソッド"
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
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9972a9d97f94a6286adc0906416349f92e6bf7ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="71793-102">ICorProfilerInfo::GetClassFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="71793-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="71793-103">指定したメタデータ トークン、クラスの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="71793-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="71793-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="71793-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="71793-105">使用して[icorprofilerinfo 2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="71793-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71793-106">構文</span><span class="sxs-lookup"><span data-stu-id="71793-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71793-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71793-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="71793-108">[in]クラスを含むモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="71793-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="71793-109">[in]`mdTypeDef`クラスを参照するメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="71793-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="71793-110">[out]クラスの ID へのポインター</span><span class="sxs-lookup"><span data-stu-id="71793-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71793-111">コメント</span><span class="sxs-lookup"><span data-stu-id="71793-111">Remarks</span></span>  
 <span data-ttu-id="71793-112">このメソッドは使用されなくなりました。代わりに、`ICorProfilerInfo2::GetClassFromTokenAndTypeArgs`すべての種類。</span><span class="sxs-lookup"><span data-stu-id="71793-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71793-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="71793-113">Requirements</span></span>  
 <span data-ttu-id="71793-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="71793-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71793-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71793-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71793-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71793-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71793-117">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="71793-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71793-118">参照</span><span class="sxs-lookup"><span data-stu-id="71793-118">See Also</span></span>  
 [<span data-ttu-id="71793-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71793-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
