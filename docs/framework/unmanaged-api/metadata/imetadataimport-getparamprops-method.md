---
title: IMetaDataImport::GetParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95850448504fd863f2726a7fb7574436476a6dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449326"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="e9c33-102">IMetaDataImport::GetParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="e9c33-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="e9c33-103">指定した ParamDef トークンによって参照されるパラメーターのメタデータ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e9c33-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c33-104">構文</span><span class="sxs-lookup"><span data-stu-id="e9c33-104">Syntax</span></span>  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9c33-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9c33-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e9c33-106">[in]メタデータを返すパラメーターを表す ParamDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="e9c33-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="e9c33-107">[out]パラメーターを受け取るメソッドを表す MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e9c33-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="e9c33-108">[out]メソッドの引数リストで、パラメーターの序数の位置。</span><span class="sxs-lookup"><span data-stu-id="e9c33-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="e9c33-109">[out]パラメーターの名前を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="e9c33-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e9c33-110">[in]要求されたサイズのワイド文字単位`szName`です。</span><span class="sxs-lookup"><span data-stu-id="e9c33-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="e9c33-111">[out]ワイド文字で返されるサイズ`szName`です。</span><span class="sxs-lookup"><span data-stu-id="e9c33-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="e9c33-112">[out]パラメーターに関連付けられている任意の属性フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e9c33-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="e9c33-113">[out]パラメーターを指定するフラグへのポインター、<xref:System.ValueType>です。</span><span class="sxs-lookup"><span data-stu-id="e9c33-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e9c33-114">[out]パラメーターによって返される定数文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e9c33-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="e9c33-115">[out]サイズ`ppValue`ワイド文字、または場合は 0 で`ppValue`文字列を保持しません。</span><span class="sxs-lookup"><span data-stu-id="e9c33-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9c33-116">要件</span><span class="sxs-lookup"><span data-stu-id="e9c33-116">Requirements</span></span>  
 <span data-ttu-id="e9c33-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9c33-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9c33-118">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e9c33-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9c33-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e9c33-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9c33-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9c33-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c33-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9c33-121">See Also</span></span>  
 [<span data-ttu-id="e9c33-122">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9c33-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e9c33-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9c33-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
