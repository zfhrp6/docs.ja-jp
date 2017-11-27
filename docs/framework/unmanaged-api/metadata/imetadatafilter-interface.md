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
ms.openlocfilehash: 7c0afbb9be9af3ffe69ddfcac85b70de53a391ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="79c6f-102">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79c6f-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="79c6f-103">メタデータ トークンにマークを付け、フィルター処理をして、既に実行されたアクションが繰り返し行われないようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="79c6f-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79c6f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="79c6f-104">Methods</span></span>  
  
|<span data-ttu-id="79c6f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="79c6f-105">Method</span></span>|<span data-ttu-id="79c6f-106">説明</span><span class="sxs-lookup"><span data-stu-id="79c6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79c6f-107">IsTokenMarked メソッド</span><span class="sxs-lookup"><span data-stu-id="79c6f-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="79c6f-108">指定したメタデータ トークンが処理されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="79c6f-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="79c6f-109">MarkToken メソッド</span><span class="sxs-lookup"><span data-stu-id="79c6f-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="79c6f-110">指定したメタデータ トークンが処理されたことを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="79c6f-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="79c6f-111">UnmarkAll メソッド</span><span class="sxs-lookup"><span data-stu-id="79c6f-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="79c6f-112">現在のメタデータ スコープ内のすべてのトークンからの処理のマークを削除します。</span><span class="sxs-lookup"><span data-stu-id="79c6f-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79c6f-113">要件</span><span class="sxs-lookup"><span data-stu-id="79c6f-113">Requirements</span></span>  
 <span data-ttu-id="79c6f-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="79c6f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79c6f-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="79c6f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79c6f-116">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="79c6f-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79c6f-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79c6f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c6f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="79c6f-118">See Also</span></span>  
 [<span data-ttu-id="79c6f-119">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79c6f-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
