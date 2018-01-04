---
title: "ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f8a89532999f599c8ec595fa709044b7d13a53a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="9ec25-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="9ec25-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="9ec25-103">マッピングの情報ソースへのトークンのスパンの特別なカスタム データ セクションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="9ec25-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="9ec25-104">閉じた後は、以上のマッピング情報を追加できます。</span><span class="sxs-lookup"><span data-stu-id="9ec25-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec25-105">構文</span><span class="sxs-lookup"><span data-stu-id="9ec25-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9ec25-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ec25-106">Return Value</span></span>  
 <span data-ttu-id="9ec25-107">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="9ec25-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec25-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="9ec25-108">Requirements</span></span>  
 <span data-ttu-id="9ec25-109">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9ec25-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec25-110">参照</span><span class="sxs-lookup"><span data-stu-id="9ec25-110">See Also</span></span>  
 [<span data-ttu-id="9ec25-111">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ec25-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
