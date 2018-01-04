---
title: "IMetaDataEmit::Merge メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Merge
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f05f2e39365b021e902b2bdaa41cda481b5af8b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="f9dc9-102">IMetaDataEmit::Merge メソッド</span><span class="sxs-lookup"><span data-stu-id="f9dc9-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="f9dc9-103">指定されたインポートされたスコープをマージするスコープの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="f9dc9-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9dc9-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9dc9-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9dc9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9dc9-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="f9dc9-106">[in]ポインター、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)オブジェクトをマージするインポートされたスコープを識別します。</span><span class="sxs-lookup"><span data-stu-id="f9dc9-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="f9dc9-107">[in]ポインター、 [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)トークンの再マップを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f9dc9-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="f9dc9-108">[in]ポインター、 <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown`エラーを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f9dc9-108">[in] A pointer to an <!--<<!--zzxref:IUnknown --> `IUnknown`>--> `IUnknown` object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9dc9-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f9dc9-109">Remarks</span></span>  
 <span data-ttu-id="f9dc9-110">呼び出す[imetadataemit::mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)を 1 つのスコープにメタデータのマージをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="f9dc9-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9dc9-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="f9dc9-111">Requirements</span></span>  
 <span data-ttu-id="f9dc9-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9dc9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9dc9-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f9dc9-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9dc9-114">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f9dc9-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9dc9-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9dc9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9dc9-116">参照</span><span class="sxs-lookup"><span data-stu-id="f9dc9-116">See Also</span></span>  
 [<span data-ttu-id="f9dc9-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9dc9-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f9dc9-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9dc9-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
