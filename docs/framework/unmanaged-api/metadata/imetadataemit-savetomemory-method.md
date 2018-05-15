---
title: IMetaDataEmit::SaveToMemory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b680e807554a60711e61729680e9c9fcf1c8fdaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="96e26-102">IMetaDataEmit::SaveToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="96e26-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="96e26-103">指定したメモリ領域を現在のスコープ内のすべてのメタデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="96e26-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e26-104">構文</span><span class="sxs-lookup"><span data-stu-id="96e26-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96e26-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96e26-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="96e26-106">[out]メタデータの書き込みを開始する位置を示すアドレス。</span><span class="sxs-lookup"><span data-stu-id="96e26-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="96e26-107">[in]割り当てられたメモリのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="96e26-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e26-108">要件</span><span class="sxs-lookup"><span data-stu-id="96e26-108">Requirements</span></span>  
 <span data-ttu-id="96e26-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="96e26-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e26-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96e26-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96e26-111">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="96e26-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96e26-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e26-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e26-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="96e26-113">See Also</span></span>  
 [<span data-ttu-id="96e26-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96e26-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="96e26-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96e26-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
