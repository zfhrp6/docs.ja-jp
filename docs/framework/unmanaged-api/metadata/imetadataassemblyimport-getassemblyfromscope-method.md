---
title: IMetaDataAssemblyImport::GetAssemblyFromScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7322b4d0fce36f5dbef7e82f35cf9e2a1cae24a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="b2c4a-102">IMetaDataAssemblyImport::GetAssemblyFromScope メソッド</span><span class="sxs-lookup"><span data-stu-id="b2c4a-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="b2c4a-103">現在のスコープでアセンブリへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b2c4a-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c4a-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2c4a-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2c4a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2c4a-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="b2c4a-106">[out]取得したへのポインター`mdAssembly`アセンブリを識別するトークン。</span><span class="sxs-lookup"><span data-stu-id="b2c4a-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c4a-107">要件</span><span class="sxs-lookup"><span data-stu-id="b2c4a-107">Requirements</span></span>  
 <span data-ttu-id="b2c4a-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b2c4a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c4a-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2c4a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2c4a-110">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b2c4a-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2c4a-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c4a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c4a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2c4a-112">See Also</span></span>  
 [<span data-ttu-id="b2c4a-113">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2c4a-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
