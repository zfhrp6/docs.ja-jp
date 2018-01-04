---
title: "ICorProfilerInfo::GetAssemblyInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAssemblyInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3ac5bd35d12bb4c9d9308dcdff3e1fb8385f6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="6b96d-102">ICorProfilerInfo::GetAssemblyInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="6b96d-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="6b96d-103">アセンブリ ID を受け入れ、アセンブリの名前とアセンブリのマニフェスト モジュールの ID を返します。</span><span class="sxs-lookup"><span data-stu-id="6b96d-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b96d-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b96d-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b96d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b96d-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="6b96d-106">[in] アセンブリの識別子。</span><span class="sxs-lookup"><span data-stu-id="6b96d-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6b96d-107">[in] `szName` の長さ (文字数)。</span><span class="sxs-lookup"><span data-stu-id="6b96d-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6b96d-108">[out] アセンブリ名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b96d-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="6b96d-109">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="6b96d-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="6b96d-110">関数が戻るときに、この関数の中にアセンブリ名が格納されます。</span><span class="sxs-lookup"><span data-stu-id="6b96d-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="6b96d-111">[out] アセンブリを含むアプリケーション ドメインの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b96d-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="6b96d-112">[out] アセンブリのマニフェスト モジュールの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b96d-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b96d-113">コメント</span><span class="sxs-lookup"><span data-stu-id="6b96d-113">Remarks</span></span>  
 <span data-ttu-id="6b96d-114">このメソッドから制御が戻った後で、`szName` バッファーのサイズが十分で、アセンブリの完全名を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b96d-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="6b96d-115">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="6b96d-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="6b96d-116">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetAssemblyInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6b96d-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="6b96d-117">別の方法として、最初に `GetAssemblyInfo` を長さゼロの `szName` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="6b96d-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="6b96d-118">その後、バッファーのサイズを `pcchName` で返された値に基づいて調整し、`GetAssemblyInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6b96d-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b96d-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="6b96d-119">Requirements</span></span>  
 <span data-ttu-id="6b96d-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b96d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b96d-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b96d-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b96d-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b96d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b96d-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b96d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b96d-124">参照</span><span class="sxs-lookup"><span data-stu-id="6b96d-124">See Also</span></span>  
 [<span data-ttu-id="6b96d-125">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b96d-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="6b96d-126">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b96d-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6b96d-127">プロファイル</span><span class="sxs-lookup"><span data-stu-id="6b96d-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
