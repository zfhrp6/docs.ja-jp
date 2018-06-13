---
title: IMetaDataImport::GetCustomAttributeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a4ed21b6f9fd067f3357e07c5fda07d25ce868d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448404"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="00174-102">IMetaDataImport::GetCustomAttributeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="00174-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="00174-103">指定したメタデータ トークンのカスタム属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="00174-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00174-104">構文</span><span class="sxs-lookup"><span data-stu-id="00174-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00174-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00174-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="00174-106">[in] 取得するカスタム属性を表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="00174-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="00174-107">[out]\(省略可能) カスタム属性が変更されるオブジェクトを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="00174-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="00174-108">この値には、`mdCustomAttribute` を除く任意の種類のトークンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="00174-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="00174-109">[out]\(省略可能) 返されるカスタム属性の <xref:System.Type> を表す `mdMethodDef` または `mdMemberRef` メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="00174-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="00174-110">[out]\(省略可能) カスタム属性の値であるデータの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="00174-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="00174-111">[out]\(省略可能) \*`ppBlob` に返されたデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="00174-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00174-112">コメント</span><span class="sxs-lookup"><span data-stu-id="00174-112">Remarks</span></span>  
 <span data-ttu-id="00174-113">カスタム属性はデータの配列として格納され、その形式はメタデータ エンジンによって解釈されます。</span><span class="sxs-lookup"><span data-stu-id="00174-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00174-114">要件</span><span class="sxs-lookup"><span data-stu-id="00174-114">Requirements</span></span>  
 <span data-ttu-id="00174-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="00174-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00174-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00174-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00174-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="00174-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00174-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00174-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00174-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="00174-119">See Also</span></span>  
 [<span data-ttu-id="00174-120">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00174-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="00174-121">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00174-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
