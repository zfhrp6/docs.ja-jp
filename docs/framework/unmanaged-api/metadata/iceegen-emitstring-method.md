---
title: "ICeeGen::EmitString メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.EmitString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f988e54a37212beeeebfbef15e6b148021e0b759
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="fb7bc-102">ICeeGen::EmitString メソッド</span><span class="sxs-lookup"><span data-stu-id="fb7bc-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="fb7bc-103">コード ベースに、指定した文字列を出力します。</span><span class="sxs-lookup"><span data-stu-id="fb7bc-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="fb7bc-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="fb7bc-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb7bc-105">構文</span><span class="sxs-lookup"><span data-stu-id="fb7bc-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb7bc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb7bc-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="fb7bc-107">[in]出力する文字列。</span><span class="sxs-lookup"><span data-stu-id="fb7bc-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="fb7bc-108">[out]生成された文字列の相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="fb7bc-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb7bc-109">要件</span><span class="sxs-lookup"><span data-stu-id="fb7bc-109">Requirements</span></span>  
 <span data-ttu-id="fb7bc-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb7bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb7bc-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fb7bc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb7bc-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="fb7bc-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb7bc-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb7bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb7bc-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb7bc-114">See Also</span></span>  
 [<span data-ttu-id="fb7bc-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb7bc-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
