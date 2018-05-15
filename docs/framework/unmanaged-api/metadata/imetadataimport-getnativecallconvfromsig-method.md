---
title: IMetaDataImport::GetNativeCallConvFromSig メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 963d46aea4ab31e770cb845fe699208f6c8f9ac7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="495ae-102">IMetaDataImport::GetNativeCallConvFromSig メソッド</span><span class="sxs-lookup"><span data-stu-id="495ae-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="495ae-103">指定したシグネチャ ポインターで表されるメソッドのネイティブな呼び出し規則を取得します。</span><span class="sxs-lookup"><span data-stu-id="495ae-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="495ae-104">構文</span><span class="sxs-lookup"><span data-stu-id="495ae-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="495ae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="495ae-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="495ae-106">[in]呼び出し規約を返すメソッドのメタデータ署名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="495ae-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="495ae-107">[in]バイト サイズ`pvSig`です。</span><span class="sxs-lookup"><span data-stu-id="495ae-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="495ae-108">[out]ネイティブ呼び出し規則へのポインター。</span><span class="sxs-lookup"><span data-stu-id="495ae-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="495ae-109">要件</span><span class="sxs-lookup"><span data-stu-id="495ae-109">Requirements</span></span>  
 <span data-ttu-id="495ae-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="495ae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="495ae-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="495ae-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="495ae-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="495ae-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="495ae-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="495ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495ae-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="495ae-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.CallingConvention>  
 [<span data-ttu-id="495ae-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="495ae-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="495ae-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="495ae-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
