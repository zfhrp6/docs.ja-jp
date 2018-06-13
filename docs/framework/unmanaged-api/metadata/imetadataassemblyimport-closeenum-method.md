---
title: IMetaDataAssemblyImport::CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5477578491c3cbc3f5fce694820971e99b45079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444101"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="5419d-102">IMetaDataAssemblyImport::CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="5419d-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="5419d-103">指定した列挙体のインスタンスへの参照を解放します。</span><span class="sxs-lookup"><span data-stu-id="5419d-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5419d-104">構文</span><span class="sxs-lookup"><span data-stu-id="5419d-104">Syntax</span></span>  
  
```  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5419d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5419d-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="5419d-106">[in]終了する列挙体のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="5419d-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5419d-107">要件</span><span class="sxs-lookup"><span data-stu-id="5419d-107">Requirements</span></span>  
 <span data-ttu-id="5419d-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5419d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5419d-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5419d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5419d-110">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="5419d-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5419d-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5419d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5419d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5419d-112">See Also</span></span>  
 [<span data-ttu-id="5419d-113">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5419d-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
