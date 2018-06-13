---
title: IMetaDataImport::CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d81f9b0107fd927ddfda24cfd0ea3249e4c8651
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448818"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="48e88-102">IMetaDataImport::CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="48e88-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="48e88-103">指定されたハンドルによって識別される列挙子を閉じます。</span><span class="sxs-lookup"><span data-stu-id="48e88-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e88-104">構文</span><span class="sxs-lookup"><span data-stu-id="48e88-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48e88-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48e88-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="48e88-106">[in]列挙子を閉じるのハンドルです。</span><span class="sxs-lookup"><span data-stu-id="48e88-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48e88-107">コメント</span><span class="sxs-lookup"><span data-stu-id="48e88-107">Remarks</span></span>  
 <span data-ttu-id="48e88-108">指定されたハンドル`hEnum`以前から取得された`Enum`*名前*を呼び出す (たとえば、 [imetadataimport::enumtypedefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md))。</span><span class="sxs-lookup"><span data-stu-id="48e88-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e88-109">要件</span><span class="sxs-lookup"><span data-stu-id="48e88-109">Requirements</span></span>  
 <span data-ttu-id="48e88-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="48e88-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e88-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="48e88-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48e88-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="48e88-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48e88-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e88-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e88-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="48e88-114">See Also</span></span>  
 [<span data-ttu-id="48e88-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48e88-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="48e88-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48e88-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
