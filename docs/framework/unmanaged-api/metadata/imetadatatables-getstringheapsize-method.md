---
title: IMetaDataTables::GetStringHeapSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d814a741bc88bb50bfe9ddc3db57635a7266a82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449921"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="96464-102">IMetaDataTables::GetStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="96464-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="96464-103">文字列ヒープのバイト単位のサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="96464-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96464-104">構文</span><span class="sxs-lookup"><span data-stu-id="96464-104">Syntax</span></span>  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96464-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96464-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="96464-106">[out]文字列ヒープのバイト単位のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="96464-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96464-107">要件</span><span class="sxs-lookup"><span data-stu-id="96464-107">Requirements</span></span>  
 <span data-ttu-id="96464-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="96464-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96464-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96464-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96464-110">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="96464-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96464-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96464-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96464-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="96464-112">See Also</span></span>  
 [<span data-ttu-id="96464-113">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96464-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="96464-114">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96464-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
