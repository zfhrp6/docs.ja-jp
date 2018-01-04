---
title: "ICeeGen::GetMethodBuffer メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23beea4bd991b21b30375c9297efb945c3dbab75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="b2360-102">ICeeGen::GetMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="b2360-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="b2360-103">指定の相対仮想アドレスのメソッドを適切なサイズのバッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="b2360-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="b2360-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b2360-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2360-105">構文</span><span class="sxs-lookup"><span data-stu-id="b2360-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2360-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2360-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="b2360-107">[in]バッファーを取得するメソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="b2360-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b2360-108">[out]返されたバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b2360-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2360-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="b2360-109">Requirements</span></span>  
 <span data-ttu-id="b2360-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b2360-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2360-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2360-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2360-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b2360-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2360-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2360-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2360-114">参照</span><span class="sxs-lookup"><span data-stu-id="b2360-114">See Also</span></span>  
 [<span data-ttu-id="b2360-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2360-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
