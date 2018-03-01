---
title: "IMetaDataEmit2::SaveDelta メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31b06f014a4638fd7f947e8188730c583183f176
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="18828-102">IMetaDataEmit2::SaveDelta メソッド</span><span class="sxs-lookup"><span data-stu-id="18828-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="18828-103">エディット コンティニュの現在のセッションからの変更を指定したファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="18828-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18828-104">構文</span><span class="sxs-lookup"><span data-stu-id="18828-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18828-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="18828-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="18828-106">[in]保存先となるファイル名を変更します。</span><span class="sxs-lookup"><span data-stu-id="18828-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="18828-107">[in]予約されています。</span><span class="sxs-lookup"><span data-stu-id="18828-107">[in] Reserved.</span></span> <span data-ttu-id="18828-108">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="18828-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18828-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="18828-109">Requirements</span></span>  
 <span data-ttu-id="18828-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="18828-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18828-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18828-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18828-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="18828-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18828-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18828-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18828-114">参照</span><span class="sxs-lookup"><span data-stu-id="18828-114">See Also</span></span>  
 [<span data-ttu-id="18828-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18828-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="18828-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18828-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
