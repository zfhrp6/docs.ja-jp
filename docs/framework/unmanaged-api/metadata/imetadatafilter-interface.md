---
title: "IMetaDataFilter インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter
helpviewer_keywords: IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0918802a146940fb7579279e56f752bd114c746c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="feba3-102">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="feba3-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="feba3-103">メタデータ トークンにマークを付け、フィルター処理をして、既に実行されたアクションが繰り返し行われないようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="feba3-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="feba3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="feba3-104">Methods</span></span>  
  
|<span data-ttu-id="feba3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="feba3-105">Method</span></span>|<span data-ttu-id="feba3-106">説明</span><span class="sxs-lookup"><span data-stu-id="feba3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="feba3-107">IsTokenMarked メソッド</span><span class="sxs-lookup"><span data-stu-id="feba3-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="feba3-108">指定したメタデータ トークンが処理されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="feba3-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="feba3-109">MarkToken メソッド</span><span class="sxs-lookup"><span data-stu-id="feba3-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="feba3-110">指定したメタデータ トークンが処理されたことを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="feba3-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="feba3-111">UnmarkAll メソッド</span><span class="sxs-lookup"><span data-stu-id="feba3-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="feba3-112">現在のメタデータ スコープ内のすべてのトークンからの処理のマークを削除します。</span><span class="sxs-lookup"><span data-stu-id="feba3-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="feba3-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="feba3-113">Requirements</span></span>  
 <span data-ttu-id="feba3-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="feba3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feba3-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="feba3-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="feba3-116">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="feba3-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="feba3-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feba3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feba3-118">参照</span><span class="sxs-lookup"><span data-stu-id="feba3-118">See Also</span></span>  
 [<span data-ttu-id="feba3-119">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="feba3-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
