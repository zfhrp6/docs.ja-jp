---
title: "IMetaDataImport::GetInterfaceImplProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: afc73536f332bd24fadee33d6321a106ccd175f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="d73c0-102">IMetaDataImport::GetInterfaceImplProps メソッド</span><span class="sxs-lookup"><span data-stu-id="d73c0-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="d73c0-103">メタデータ トークンへのポインターを取得、<xref:System.Type>指定したメソッドを実装し、そのメソッドを宣言するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d73c0-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d73c0-104">構文</span><span class="sxs-lookup"><span data-stu-id="d73c0-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d73c0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d73c0-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="d73c0-106">[in]クラスとインターフェイスのトークンを返すメソッドを表すメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="d73c0-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d73c0-107">[out]メソッドを実装するクラスを表すメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="d73c0-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="d73c0-108">[out]実装されたメソッドを定義するインターフェイスを表すメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="d73c0-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d73c0-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="d73c0-109">Requirements</span></span>  
 <span data-ttu-id="d73c0-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d73c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d73c0-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d73c0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d73c0-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d73c0-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d73c0-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d73c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73c0-114">参照</span><span class="sxs-lookup"><span data-stu-id="d73c0-114">See Also</span></span>  
 [<span data-ttu-id="d73c0-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d73c0-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d73c0-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d73c0-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
