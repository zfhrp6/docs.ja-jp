---
title: IMetaDataAssemblyImport::EnumExportedTypes メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9aef8c40be2456532bd6df6feb8d286cdaeefa7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445632"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="3d0d4-102">IMetaDataAssemblyImport::EnumExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="3d0d4-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="3d0d4-103">現在のメタデータ スコープ内のアセンブリ マニフェストで参照されているエクスポートされた型を列挙します。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d0d4-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d0d4-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d0d4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d0d4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3d0d4-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3d0d4-107">これは null を指定する必要があるときの値、`EnumExportedTypes`メソッドは、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="3d0d4-108">[out]列挙体`mdExportedType`メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3d0d4-109">[in]最大数`mdExportedType`に配置可能なトークン、`rExportedTypes`配列。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3d0d4-110">[out]数`mdExportedType`にトークンが実際に配置されます`rExportedTypes`です。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d0d4-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d0d4-111">Return Value</span></span>  
  
|<span data-ttu-id="3d0d4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d0d4-112">HRESULT</span></span>|<span data-ttu-id="3d0d4-113">説明</span><span class="sxs-lookup"><span data-stu-id="3d0d4-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3d0d4-114">`EnumExportedTypes` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3d0d4-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3d0d4-116">この場合、`pcTokens`は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d0d4-117">要件</span><span class="sxs-lookup"><span data-stu-id="3d0d4-117">Requirements</span></span>  
 <span data-ttu-id="3d0d4-118">**Platform:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d0d4-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d0d4-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3d0d4-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d0d4-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="3d0d4-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d0d4-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d0d4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d0d4-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d0d4-122">See Also</span></span>  
 [<span data-ttu-id="3d0d4-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d0d4-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
