---
title: "IMetaDataImport::GetFieldProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetFieldProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d5874169e0f8c452b177309702444ea84858557e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="6aeff-102">IMetaDataImport::GetFieldProps メソッド</span><span class="sxs-lookup"><span data-stu-id="6aeff-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="6aeff-103">指定した FieldDef トークンによって参照されるフィールドに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="6aeff-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aeff-104">構文</span><span class="sxs-lookup"><span data-stu-id="6aeff-104">Syntax</span></span>  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6aeff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6aeff-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="6aeff-106">[in]関連付けられているメタデータを取得するフィールドを表す FieldDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="6aeff-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="6aeff-107">[out]フィールドが属するクラスの型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6aeff-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="6aeff-108">[out]フィールドの名前です。</span><span class="sxs-lookup"><span data-stu-id="6aeff-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="6aeff-109">[in]サイズのバッファーのワイド文字*szField*です。</span><span class="sxs-lookup"><span data-stu-id="6aeff-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="6aeff-110">[out]返されたバッファーの実際のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6aeff-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="6aeff-111">[out]フィールドのメタデータに関連付けられるフラグ。</span><span class="sxs-lookup"><span data-stu-id="6aeff-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="6aeff-112">[in]フィールドを説明するバイナリ メタデータ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6aeff-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="6aeff-113">[out]バイト サイズ`ppvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="6aeff-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="6aeff-114">[out]フィールドの値の型を指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="6aeff-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6aeff-115">[out]フィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="6aeff-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="6aeff-116">[out]サイズの文字で`ppValue`文字列が存在しない場合は 0 です。</span><span class="sxs-lookup"><span data-stu-id="6aeff-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aeff-117">要件</span><span class="sxs-lookup"><span data-stu-id="6aeff-117">Requirements</span></span>  
 <span data-ttu-id="6aeff-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6aeff-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aeff-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6aeff-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6aeff-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6aeff-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6aeff-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aeff-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aeff-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6aeff-122">See Also</span></span>  
 [<span data-ttu-id="6aeff-123">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6aeff-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6aeff-124">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6aeff-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
