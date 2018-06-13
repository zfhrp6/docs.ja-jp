---
title: IMetaDataImport::GetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b031fc35a4687a8535e3cb5e9ef2a53bab9fe376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445508"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="aee98-102">IMetaDataImport::GetClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="aee98-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="aee98-103">指定した TypeDef トークンによって参照されるクラスのレイアウト情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="aee98-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aee98-104">構文</span><span class="sxs-lookup"><span data-stu-id="aee98-104">Syntax</span></span>  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aee98-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aee98-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="aee98-106">[in]返すレイアウトを持つクラスの TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="aee98-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="aee98-107">[out]値 1、2、4、8、またはクラスのパック サイズを表す、16 のいずれか。</span><span class="sxs-lookup"><span data-stu-id="aee98-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="aee98-108">[out]配列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)値。</span><span class="sxs-lookup"><span data-stu-id="aee98-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="aee98-109">[in] `rFieldOffset` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="aee98-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="aee98-110">[out]返される要素の数`rFieldOffset`です。</span><span class="sxs-lookup"><span data-stu-id="aee98-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="aee98-111">[out]によって表されるクラスのバイト サイズ`td`です。</span><span class="sxs-lookup"><span data-stu-id="aee98-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aee98-112">要件</span><span class="sxs-lookup"><span data-stu-id="aee98-112">Requirements</span></span>  
 <span data-ttu-id="aee98-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aee98-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aee98-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aee98-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aee98-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="aee98-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aee98-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aee98-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee98-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="aee98-117">See Also</span></span>  
 [<span data-ttu-id="aee98-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aee98-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="aee98-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aee98-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
