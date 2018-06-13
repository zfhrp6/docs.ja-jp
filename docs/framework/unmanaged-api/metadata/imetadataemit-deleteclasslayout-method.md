---
title: IMetaDataEmit::DeleteClassLayout メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 663f2de5acb3aac92c29a19f5f5db16b5355fe89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444784"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="7dfde-102">IMetaDataEmit::DeleteClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="7dfde-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="7dfde-103">指定したトークンによって表される型のクラス レイアウト メタデータ シグネチャを破棄します。</span><span class="sxs-lookup"><span data-stu-id="7dfde-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dfde-104">構文</span><span class="sxs-lookup"><span data-stu-id="7dfde-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dfde-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7dfde-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7dfde-106">[in]`mdTypeDef`クラス レイアウトの削除対象の型を表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="7dfde-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dfde-107">要件</span><span class="sxs-lookup"><span data-stu-id="7dfde-107">Requirements</span></span>  
 <span data-ttu-id="7dfde-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7dfde-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dfde-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7dfde-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7dfde-110">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="7dfde-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7dfde-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dfde-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfde-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dfde-112">See Also</span></span>  
 [<span data-ttu-id="7dfde-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dfde-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7dfde-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dfde-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
