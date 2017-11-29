---
title: "ICorProfilerInfo::GetClassFromToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 761c537f0b3aba529a8a3a862a1a975ddd1c6303
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="a628d-102">ICorProfilerInfo::GetClassFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="a628d-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="a628d-103">指定したメタデータ トークン、クラスの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="a628d-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="a628d-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="a628d-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a628d-105">使用して[icorprofilerinfo 2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="a628d-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a628d-106">構文</span><span class="sxs-lookup"><span data-stu-id="a628d-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a628d-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a628d-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a628d-108">[in]クラスを含むモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="a628d-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="a628d-109">[in]`mdTypeDef`クラスを参照するメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="a628d-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="a628d-110">[out]クラスの ID へのポインター</span><span class="sxs-lookup"><span data-stu-id="a628d-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a628d-111">コメント</span><span class="sxs-lookup"><span data-stu-id="a628d-111">Remarks</span></span>  
 <span data-ttu-id="a628d-112">このメソッドは使用されなくなりました。代わりに、`ICorProfilerInfo2::GetClassFromTokenAndTypeArgs`すべての種類。</span><span class="sxs-lookup"><span data-stu-id="a628d-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a628d-113">要件</span><span class="sxs-lookup"><span data-stu-id="a628d-113">Requirements</span></span>  
 <span data-ttu-id="a628d-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a628d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a628d-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a628d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a628d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a628d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a628d-117">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="a628d-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a628d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a628d-118">See Also</span></span>  
 [<span data-ttu-id="a628d-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a628d-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
