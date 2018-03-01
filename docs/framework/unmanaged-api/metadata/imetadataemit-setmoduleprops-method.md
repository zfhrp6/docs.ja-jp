---
title: "IMetaDataEmit::SetModuleProps メソッド"
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
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e67acee8092fa20500038bb25e542c3dddb3233e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="13a43-102">IMetaDataEmit::SetModuleProps メソッド</span><span class="sxs-lookup"><span data-stu-id="13a43-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="13a43-103">前回の呼び出しで定義されているモジュールへの参照を更新[imetadataemit::definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="13a43-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a43-104">構文</span><span class="sxs-lookup"><span data-stu-id="13a43-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13a43-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="13a43-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="13a43-106">[in]Unicode でモジュールの名前です。</span><span class="sxs-lookup"><span data-stu-id="13a43-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="13a43-107">これは、ファイル名のみと完全なパス名ではありません。</span><span class="sxs-lookup"><span data-stu-id="13a43-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13a43-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="13a43-108">Requirements</span></span>  
 <span data-ttu-id="13a43-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="13a43-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a43-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13a43-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13a43-111">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="13a43-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13a43-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a43-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a43-113">参照</span><span class="sxs-lookup"><span data-stu-id="13a43-113">See Also</span></span>  
 [<span data-ttu-id="13a43-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13a43-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="13a43-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13a43-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
