---
title: IMetaDataImport::GetPropertyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7312cbd31a04365801b0380d5914966f36679560
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449456"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="cdb4a-102">IMetaDataImport::GetPropertyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="cdb4a-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="cdb4a-103">指定したトークンによって表されるプロパティのメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb4a-104">構文</span><span class="sxs-lookup"><span data-stu-id="cdb4a-104">Syntax</span></span>  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdb4a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cdb4a-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="cdb4a-106">[in]メタデータを取得するプロパティを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="cdb4a-107">[out]プロパティを実装する型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="cdb4a-108">[out]プロパティ名を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="cdb4a-109">[in]ワイド文字単位のサイズ`szProperty`です。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="cdb4a-110">[out]ワイド文字数で返される`szProperty`です。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="cdb4a-111">[out]プロパティに適用される属性フラグのいずれかへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="cdb4a-112">この値からビットマスクである、 [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="cdb4a-113">[out]プロパティのメタデータ署名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="cdb4a-114">[out]返されるバイト数`ppvSig`です。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="cdb4a-115">[out]プロパティの既定値は、定数の型を指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="cdb4a-116">この値は CorElementType 列挙型です。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="cdb4a-117">[out]このプロパティの既定値を格納するバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="cdb4a-118">[out]ワイド文字単位のサイズ`ppDefaultValue`場合は、 `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING; は、それ以外の場合、この値は使用されません。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="cdb4a-119">その場合の長さ`ppDefaultValue`で指定された型から推論`pdwCPlusTypeFlag`です。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="cdb4a-120">[out]プロパティの set アクセサー メソッドを表す MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="cdb4a-121">[out]プロパティの get アクセサー メソッドを表す MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="cdb4a-122">[out]プロパティに関連付けられたその他のメソッドを表す MethodDef トークンの配列。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cdb4a-123">[in] `rmdOtherMethod` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="cdb4a-124">すべてのメソッドを保持するために十分な大きさの配列を指定しない場合は警告なしスキップされます。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="cdb4a-125">[out]MethodDef トークンで返される数`rmdOtherMethod`です。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdb4a-126">要件</span><span class="sxs-lookup"><span data-stu-id="cdb4a-126">Requirements</span></span>  
 <span data-ttu-id="cdb4a-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdb4a-128">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cdb4a-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cdb4a-129">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="cdb4a-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cdb4a-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdb4a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb4a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdb4a-131">See Also</span></span>  
 [<span data-ttu-id="cdb4a-132">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cdb4a-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cdb4a-133">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cdb4a-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
