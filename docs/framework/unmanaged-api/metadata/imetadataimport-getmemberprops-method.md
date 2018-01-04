---
title: "IMetaDataImport::GetMemberProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 543929390977fc593e86947feece06f43bc0cad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="99c98-102">IMetaDataImport::GetMemberProps メソッド</span><span class="sxs-lookup"><span data-stu-id="99c98-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="99c98-103">名前、バイナリ シグネチャ、相対仮想アドレスをなどのメタデータ情報を取得、<xref:System.Type>指定したメタデータ トークンによって参照されるメンバー。</span><span class="sxs-lookup"><span data-stu-id="99c98-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c98-104">構文</span><span class="sxs-lookup"><span data-stu-id="99c98-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="99c98-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="99c98-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="99c98-106">[in]関連付けられているメタデータを取得するメンバーを参照するトークンです。</span><span class="sxs-lookup"><span data-stu-id="99c98-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="99c98-107">[out]メンバーのクラスを表すメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99c98-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="99c98-108">[out]メンバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="99c98-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="99c98-109">[in]ワイド文字単位のサイズ、`szMember`バッファー。</span><span class="sxs-lookup"><span data-stu-id="99c98-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="99c98-110">[out]返される名前のワイド文字単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="99c98-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="99c98-111">[out]いずれかのメンバーに適用される値にフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="99c98-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="99c98-112">[out]メンバーのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99c98-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="99c98-113">[out]バイト サイズ`ppvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="99c98-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="99c98-114">[out]メンバーの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="99c98-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="99c98-115">[out]メンバーに関連付けられているどのメソッド実装フラグ。</span><span class="sxs-lookup"><span data-stu-id="99c98-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="99c98-116">[out]マークするフラグを<xref:System.ValueType>です。</span><span class="sxs-lookup"><span data-stu-id="99c98-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="99c98-117">[out]このメンバーによって返される定数文字列値。</span><span class="sxs-lookup"><span data-stu-id="99c98-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="99c98-118">[out]サイズの文字`ppValue`、または場合は 0`ppValue`文字列を保持しません。</span><span class="sxs-lookup"><span data-stu-id="99c98-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99c98-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="99c98-119">Requirements</span></span>  
 <span data-ttu-id="99c98-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="99c98-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99c98-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="99c98-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99c98-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="99c98-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99c98-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99c98-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c98-124">参照</span><span class="sxs-lookup"><span data-stu-id="99c98-124">See Also</span></span>  
 [<span data-ttu-id="99c98-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99c98-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="99c98-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99c98-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
