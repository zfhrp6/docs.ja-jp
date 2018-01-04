---
title: "IMetaDataAssemblyImport::EnumExportedTypes メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumExportedTypes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54b5a51dc0a12bb4c159b61252c9db0a82f03518
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="86724-102">IMetaDataAssemblyImport::EnumExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="86724-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="86724-103">現在のメタデータ スコープ内のアセンブリ マニフェストで参照されているエクスポートされた型を列挙します。</span><span class="sxs-lookup"><span data-stu-id="86724-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86724-104">構文</span><span class="sxs-lookup"><span data-stu-id="86724-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86724-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86724-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="86724-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="86724-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="86724-107">これは null を指定する必要があるときの値、`EnumExportedTypes`メソッドは、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="86724-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="86724-108">[out]列挙体`mdExportedType`メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="86724-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="86724-109">[in]最大数`mdExportedType`に配置可能なトークン、`rExportedTypes`配列。</span><span class="sxs-lookup"><span data-stu-id="86724-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="86724-110">[out]数`mdExportedType`にトークンが実際に配置されます`rExportedTypes`です。</span><span class="sxs-lookup"><span data-stu-id="86724-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86724-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="86724-111">Return Value</span></span>  
  
|<span data-ttu-id="86724-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86724-112">HRESULT</span></span>|<span data-ttu-id="86724-113">説明</span><span class="sxs-lookup"><span data-stu-id="86724-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="86724-114">`EnumExportedTypes`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="86724-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="86724-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="86724-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="86724-116">この場合、`pcTokens`は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="86724-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86724-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="86724-117">Requirements</span></span>  
 <span data-ttu-id="86724-118">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="86724-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86724-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="86724-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86724-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="86724-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86724-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86724-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86724-122">参照</span><span class="sxs-lookup"><span data-stu-id="86724-122">See Also</span></span>  
 [<span data-ttu-id="86724-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86724-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
