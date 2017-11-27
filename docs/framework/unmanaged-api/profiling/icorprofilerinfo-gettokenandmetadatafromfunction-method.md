---
title: "ICorProfilerInfo::GetTokenAndMetadataFromFunction メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 585b28161814045777cf2294f78bafc3229bfae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="06464-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="06464-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="06464-103">メタデータ インターフェイス インスタンスの指定された関数のトークンに対して使用できるメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="06464-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06464-104">構文</span><span class="sxs-lookup"><span data-stu-id="06464-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06464-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="06464-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="06464-106">[in]メタデータ インターフェイスには、メタデータ トークンを取得する対象の関数の ID。</span><span class="sxs-lookup"><span data-stu-id="06464-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="06464-107">[in]インスタンスを取得するメタデータ インターフェイスの参照 ID です。</span><span class="sxs-lookup"><span data-stu-id="06464-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="06464-108">[out]指定した関数のトークンに対して使用できるメタデータ インターフェイスのインスタンスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="06464-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="06464-109">[out]指定された関数のメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="06464-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06464-110">要件</span><span class="sxs-lookup"><span data-stu-id="06464-110">Requirements</span></span>  
 <span data-ttu-id="06464-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="06464-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06464-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06464-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06464-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06464-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06464-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06464-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06464-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="06464-115">See Also</span></span>  
 [<span data-ttu-id="06464-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="06464-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
