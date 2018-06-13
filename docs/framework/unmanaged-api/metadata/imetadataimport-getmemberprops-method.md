---
title: IMetaDataImport::GetMemberProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448459"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="8bd1d-102">IMetaDataImport::GetMemberProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8bd1d-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="8bd1d-103">名前、バイナリ シグネチャ、相対仮想アドレスをなどのメタデータ情報を取得、<xref:System.Type>指定したメタデータ トークンによって参照されるメンバー。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd1d-104">構文</span><span class="sxs-lookup"><span data-stu-id="8bd1d-104">Syntax</span></span>  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bd1d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8bd1d-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="8bd1d-106">[in]関連付けられているメタデータを取得するメンバーを参照するトークンです。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="8bd1d-107">[out]メンバーのクラスを表すメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="8bd1d-108">[out]メンバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="8bd1d-109">[in]ワイド文字単位のサイズ、`szMember`バッファー。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="8bd1d-110">[out]返される名前のワイド文字単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="8bd1d-111">[out]いずれかのメンバーに適用される値にフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="8bd1d-112">[out]メンバーのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="8bd1d-113">[out]バイト サイズ`ppvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="8bd1d-114">[out]メンバーの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="8bd1d-115">[out]メンバーに関連付けられているどのメソッド実装フラグ。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="8bd1d-116">[out]マークするフラグを<xref:System.ValueType>です。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8bd1d-117">[out]このメンバーによって返される定数文字列値。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="8bd1d-118">[out]サイズの文字`ppValue`、または場合は 0`ppValue`文字列を保持しません。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bd1d-119">要件</span><span class="sxs-lookup"><span data-stu-id="8bd1d-119">Requirements</span></span>  
 <span data-ttu-id="8bd1d-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bd1d-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8bd1d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bd1d-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8bd1d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bd1d-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bd1d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd1d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bd1d-124">See Also</span></span>  
 [<span data-ttu-id="8bd1d-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bd1d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8bd1d-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bd1d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
