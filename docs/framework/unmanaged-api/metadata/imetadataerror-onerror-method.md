---
title: "IMetaDataError::OnError メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataError.OnError
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6e136f3fd76b9eb2be1e49a48316dc65c481fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="8ca2c-102">IMetaDataError::OnError メソッド</span><span class="sxs-lookup"><span data-stu-id="8ca2c-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="8ca2c-103">メタデータのマージ中に発生したエラーの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca2c-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ca2c-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ca2c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ca2c-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="8ca2c-106">[in]呼び出し元のメソッドに HRESULT エラー値が返されます。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="8ca2c-107">[in]そのエラーが発生したときにマージされたコード オブジェクトのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca2c-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="8ca2c-108">Requirements</span></span>  
 <span data-ttu-id="8ca2c-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ca2c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca2c-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ca2c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ca2c-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="8ca2c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ca2c-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca2c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca2c-113">参照</span><span class="sxs-lookup"><span data-stu-id="8ca2c-113">See Also</span></span>  
 [<span data-ttu-id="8ca2c-114">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ca2c-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
