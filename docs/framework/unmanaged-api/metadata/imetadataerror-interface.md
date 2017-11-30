---
title: "IMetaDataError インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataError
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataError
helpviewer_keywords: IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ae90221a1b305fdf09ae9583e720a2092289362
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="14e9a-102">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14e9a-102">IMetaDataError Interface</span></span>
<span data-ttu-id="14e9a-103">メタデータのマージ中にエラーを報告するためのコールバック機構を提供します。</span><span class="sxs-lookup"><span data-stu-id="14e9a-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14e9a-104">`IMetaDataError`クライアントによってインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14e9a-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14e9a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="14e9a-105">Methods</span></span>  
  
|<span data-ttu-id="14e9a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="14e9a-106">Method</span></span>|<span data-ttu-id="14e9a-107">説明</span><span class="sxs-lookup"><span data-stu-id="14e9a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14e9a-108">OnError メソッド</span><span class="sxs-lookup"><span data-stu-id="14e9a-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="14e9a-109">メタデータのマージ中に発生したエラーの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="14e9a-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14e9a-110">要件</span><span class="sxs-lookup"><span data-stu-id="14e9a-110">Requirements</span></span>  
 <span data-ttu-id="14e9a-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="14e9a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14e9a-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14e9a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14e9a-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="14e9a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14e9a-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14e9a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e9a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="14e9a-115">See Also</span></span>  
 [<span data-ttu-id="14e9a-116">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14e9a-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
