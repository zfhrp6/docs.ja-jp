---
title: "IMetaDataImport::CountEnum メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.CountEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26e826417e6fb48eb261278988bc7c351ee663aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="cab22-102">IMetaDataImport::CountEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="cab22-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="cab22-103">指定した列挙子によって取得された列挙体の要素の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="cab22-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cab22-104">構文</span><span class="sxs-lookup"><span data-stu-id="cab22-104">Syntax</span></span>  
  
```  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cab22-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cab22-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="cab22-106">[in]列挙子のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="cab22-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="cab22-107">[out]列挙された要素の数。</span><span class="sxs-lookup"><span data-stu-id="cab22-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cab22-108">コメント</span><span class="sxs-lookup"><span data-stu-id="cab22-108">Remarks</span></span>  
 <span data-ttu-id="cab22-109">指定されたハンドル`hEnum`以前から取得された`Enum`*名前*を呼び出す (たとえば、 [imetadataimport::enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md))。</span><span class="sxs-lookup"><span data-stu-id="cab22-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cab22-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="cab22-110">Requirements</span></span>  
 <span data-ttu-id="cab22-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cab22-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cab22-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cab22-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cab22-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="cab22-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cab22-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab22-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cab22-115">参照</span><span class="sxs-lookup"><span data-stu-id="cab22-115">See Also</span></span>  
 [<span data-ttu-id="cab22-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cab22-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cab22-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cab22-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
