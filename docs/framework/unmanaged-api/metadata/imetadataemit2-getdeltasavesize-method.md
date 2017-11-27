---
title: "IMetaDataEmit2::GetDeltaSaveSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.GetDeltaSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0a1b3aec06d6593257c82d6e3c08d6a8e2430691
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="360b6-102">IMetaDataEmit2::GetDeltaSaveSize メソッド</span><span class="sxs-lookup"><span data-stu-id="360b6-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="360b6-103">エディット コンティニュの現在のセッションを実行した結果のメタデータのサイズ変更を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="360b6-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="360b6-104">構文</span><span class="sxs-lookup"><span data-stu-id="360b6-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="360b6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="360b6-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="360b6-106">[in]1 つ、 [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)必要に応じて有効桁数のレベルを示す値。</span><span class="sxs-lookup"><span data-stu-id="360b6-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="360b6-107">.NET Framework version 2.0 では、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="360b6-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="360b6-108">[out]メタデータのサイズの変化です。</span><span class="sxs-lookup"><span data-stu-id="360b6-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="360b6-109">要件</span><span class="sxs-lookup"><span data-stu-id="360b6-109">Requirements</span></span>  
 <span data-ttu-id="360b6-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="360b6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="360b6-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="360b6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="360b6-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="360b6-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="360b6-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="360b6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="360b6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="360b6-114">See Also</span></span>  
 [<span data-ttu-id="360b6-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="360b6-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="360b6-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="360b6-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
