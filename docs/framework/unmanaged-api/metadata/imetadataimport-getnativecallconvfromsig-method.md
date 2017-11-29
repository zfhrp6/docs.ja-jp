---
title: "IMetaDataImport::GetNativeCallConvFromSig メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNativeCallConvFromSig
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5bcd54d4c0a0a1ac4dcb98e51fc25e5f3a7c7288
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="224ae-102">IMetaDataImport::GetNativeCallConvFromSig メソッド</span><span class="sxs-lookup"><span data-stu-id="224ae-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="224ae-103">指定したシグネチャ ポインターで表されるメソッドのネイティブな呼び出し規則を取得します。</span><span class="sxs-lookup"><span data-stu-id="224ae-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="224ae-104">構文</span><span class="sxs-lookup"><span data-stu-id="224ae-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="224ae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="224ae-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="224ae-106">[in]呼び出し規約を返すメソッドのメタデータ署名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="224ae-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="224ae-107">[in]バイト サイズ`pvSig`です。</span><span class="sxs-lookup"><span data-stu-id="224ae-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="224ae-108">[out]ネイティブ呼び出し規則へのポインター。</span><span class="sxs-lookup"><span data-stu-id="224ae-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="224ae-109">要件</span><span class="sxs-lookup"><span data-stu-id="224ae-109">Requirements</span></span>  
 <span data-ttu-id="224ae-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="224ae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="224ae-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="224ae-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="224ae-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="224ae-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="224ae-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="224ae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="224ae-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="224ae-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.CallingConvention>  
 [<span data-ttu-id="224ae-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="224ae-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="224ae-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="224ae-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
