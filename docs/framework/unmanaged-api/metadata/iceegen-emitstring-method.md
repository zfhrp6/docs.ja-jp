---
title: "ICeeGen::EmitString メソッド"
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
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89c53f41595416a6bb4b8d373c7d3dbcea4c4faa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="6d463-102">ICeeGen::EmitString メソッド</span><span class="sxs-lookup"><span data-stu-id="6d463-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="6d463-103">コード ベースに、指定した文字列を出力します。</span><span class="sxs-lookup"><span data-stu-id="6d463-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="6d463-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="6d463-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d463-105">構文</span><span class="sxs-lookup"><span data-stu-id="6d463-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d463-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d463-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="6d463-107">[in]出力する文字列。</span><span class="sxs-lookup"><span data-stu-id="6d463-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="6d463-108">[out]生成された文字列の相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="6d463-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d463-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="6d463-109">Requirements</span></span>  
 <span data-ttu-id="6d463-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6d463-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d463-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d463-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d463-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="6d463-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d463-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d463-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d463-114">参照</span><span class="sxs-lookup"><span data-stu-id="6d463-114">See Also</span></span>  
 [<span data-ttu-id="6d463-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d463-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
