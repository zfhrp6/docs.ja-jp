---
title: IMetaDataEmit::ApplyEditAndContinue メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c15c554e0ec135b33d671a83b5e27d0a2a89b731
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444257"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="cc9c7-102">IMetaDataEmit::ApplyEditAndContinue メソッド</span><span class="sxs-lookup"><span data-stu-id="cc9c7-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="cc9c7-103">指定されたメタデータに加えられた変更と、現在のアセンブリのスコープを更新します。</span><span class="sxs-lookup"><span data-stu-id="cc9c7-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc9c7-104">構文</span><span class="sxs-lookup"><span data-stu-id="cc9c7-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc9c7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc9c7-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="cc9c7-106">[in]ポインターを <<!--zzxref:IUnknown --> `IUnknown`>、ポータブル実行可能 (PE) ファイルからのデルタ メタデータを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="cc9c7-106">[in] Pointer to an <<!--zzxref:IUnknown --> `IUnknown`> object that represents the delta metadata from the portable executable (PE) file.</span></span>  
  
 <span data-ttu-id="cc9c7-107">デルタのメタデータは、モジュールの実際のメタデータのコピーに対して行われた変更を含むメタデータのブロックです。</span><span class="sxs-lookup"><span data-stu-id="cc9c7-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc9c7-108">要件</span><span class="sxs-lookup"><span data-stu-id="cc9c7-108">Requirements</span></span>  
 <span data-ttu-id="cc9c7-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc9c7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc9c7-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cc9c7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc9c7-111">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="cc9c7-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc9c7-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc9c7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9c7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc9c7-113">See Also</span></span>  
 [<span data-ttu-id="cc9c7-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc9c7-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="cc9c7-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc9c7-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
