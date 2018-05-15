---
title: IMetaDataTables::GetUserStringHeapSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a217a835e258052ace5b59a70cbc0fa31691d78e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="b1796-102">IMetaDataTables::GetUserStringHeapSize メソッド</span><span class="sxs-lookup"><span data-stu-id="b1796-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="b1796-103">ユーザー文字列ヒープのバイト単位のサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="b1796-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1796-104">構文</span><span class="sxs-lookup"><span data-stu-id="b1796-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1796-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b1796-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="b1796-106">[out]ユーザー文字列ヒープのバイト単位のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b1796-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1796-107">要件</span><span class="sxs-lookup"><span data-stu-id="b1796-107">Requirements</span></span>  
 <span data-ttu-id="b1796-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1796-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1796-109">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b1796-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1796-110">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b1796-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1796-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1796-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1796-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1796-112">See Also</span></span>  
 [<span data-ttu-id="b1796-113">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1796-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="b1796-114">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1796-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
