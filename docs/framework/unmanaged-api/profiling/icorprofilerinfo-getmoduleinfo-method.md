---
title: "ICorProfilerInfo::GetModuleInfo メソッド"
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
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8309b57f2940805e23010feac17b6d37f1a58af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="c0976-102">ICorProfilerInfo::GetModuleInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="c0976-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="c0976-103">モジュール ID を指定して、モジュールのファイル名とモジュールの親アセンブリの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="c0976-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0976-104">構文</span><span class="sxs-lookup"><span data-stu-id="c0976-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0976-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c0976-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c0976-106">[in] 情報が取得されるモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="c0976-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="c0976-107">[out] モジュールが読み込まれるベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="c0976-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c0976-108">[in] `szName` 戻りバッファーの長さ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="c0976-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c0976-109">[out] 返されるモジュールのファイル名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0976-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="c0976-110">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="c0976-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="c0976-111">メソッドから制御が戻るとき、このバッファーにモジュールのファイル名が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c0976-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="c0976-112">[out] モジュールの親アセンブリ ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c0976-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0976-113">コメント</span><span class="sxs-lookup"><span data-stu-id="c0976-113">Remarks</span></span>  
 <span data-ttu-id="c0976-114">動的モジュールの場合、`szName` パラメーターは空の文字列、ベース アドレスは 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="c0976-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="c0976-115">ただし、`GetModuleInfo`モジュールの ID が存在するとすぐに、メソッドを呼び出すことができます、プロファイラーを受け取るまで、親アセンブリの ID は使用できません、 [icorprofilercallback::moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="c0976-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="c0976-116">`GetModuleInfo` から制御が戻ったら、`szName` バッファーのサイズが十分で、モジュールのファイル名全体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0976-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="c0976-117">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="c0976-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="c0976-118">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetModuleInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c0976-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="c0976-119">別の方法として、最初に長さ 0 の `szName` バッファーで `GetModuleInfo` を呼び出すことで、適切なバッファーのサイズを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c0976-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="c0976-120">その後、バッファーのサイズを `pcchName` で返された値に設定し、`GetModuleInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c0976-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0976-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="c0976-121">Requirements</span></span>  
 <span data-ttu-id="c0976-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0976-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0976-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0976-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0976-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0976-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0976-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0976-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0976-126">参照</span><span class="sxs-lookup"><span data-stu-id="c0976-126">See Also</span></span>  
 [<span data-ttu-id="c0976-127">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0976-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c0976-128">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0976-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c0976-129">プロファイル</span><span class="sxs-lookup"><span data-stu-id="c0976-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [<span data-ttu-id="c0976-130">GetModuleInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="c0976-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
