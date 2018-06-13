---
title: IMetaDataTables::GetGuidHeapSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97d196769b549022ce498958fc34cf08df442d0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447091"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="da45d-102">IMetaDataTables::GetGuidHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="da45d-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="da45d-103">GUID ヒープのバイト単位のサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="da45d-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da45d-104">構文</span><span class="sxs-lookup"><span data-stu-id="da45d-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da45d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="da45d-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="da45d-106">[out]GUID ヒープのバイト単位のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="da45d-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da45d-107">要件</span><span class="sxs-lookup"><span data-stu-id="da45d-107">Requirements</span></span>  
 <span data-ttu-id="da45d-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="da45d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da45d-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="da45d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da45d-110">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="da45d-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da45d-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da45d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da45d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="da45d-112">See Also</span></span>  
 [<span data-ttu-id="da45d-113">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da45d-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="da45d-114">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="da45d-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
