---
title: IMetaDataError インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c264bfd31f8cd31bacf2d194ddbd07338569294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="eb2d6-102">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb2d6-102">IMetaDataError Interface</span></span>
<span data-ttu-id="eb2d6-103">メタデータのマージ中にエラーを報告するためのコールバック機構を提供します。</span><span class="sxs-lookup"><span data-stu-id="eb2d6-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb2d6-104">`IMetaDataError`クライアントによってインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb2d6-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb2d6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="eb2d6-105">Methods</span></span>  
  
|<span data-ttu-id="eb2d6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="eb2d6-106">Method</span></span>|<span data-ttu-id="eb2d6-107">説明</span><span class="sxs-lookup"><span data-stu-id="eb2d6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb2d6-108">OnError メソッド</span><span class="sxs-lookup"><span data-stu-id="eb2d6-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="eb2d6-109">メタデータのマージ中に発生したエラーの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="eb2d6-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb2d6-110">要件</span><span class="sxs-lookup"><span data-stu-id="eb2d6-110">Requirements</span></span>  
 <span data-ttu-id="eb2d6-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb2d6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2d6-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eb2d6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb2d6-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="eb2d6-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb2d6-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2d6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2d6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb2d6-115">See Also</span></span>  
 [<span data-ttu-id="eb2d6-116">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb2d6-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
