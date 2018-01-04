---
title: "IMetaDataConverter::GetTypeLibFromMetaData メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter.GetTypeLibFromMetaData
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e7665eabf46d4bda822dcb41125ccfcee6d8516
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="9301a-102">IMetaDataConverter::GetTypeLibFromMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="9301a-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="9301a-103">ポインターを取得、`ITypeLib`を指定したライブラリとモジュールの名前を持つタイプ ライブラリを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="9301a-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9301a-104">構文</span><span class="sxs-lookup"><span data-stu-id="9301a-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9301a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9301a-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="9301a-106">[in]タイプ ライブラリのモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="9301a-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="9301a-107">[in]タイプ ライブラリの名前。</span><span class="sxs-lookup"><span data-stu-id="9301a-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="9301a-108">[out]アドレスを受け取る場所へのポインター、`ITypeLib`をタイプ ライブラリを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="9301a-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9301a-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="9301a-109">Requirements</span></span>  
 <span data-ttu-id="9301a-110">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9301a-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9301a-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9301a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9301a-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="9301a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9301a-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9301a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9301a-114">参照</span><span class="sxs-lookup"><span data-stu-id="9301a-114">See Also</span></span>  
 [<span data-ttu-id="9301a-115">IMetaDataConverter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9301a-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
