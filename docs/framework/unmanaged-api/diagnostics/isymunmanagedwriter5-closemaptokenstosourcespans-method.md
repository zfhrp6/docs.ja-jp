---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 653dd933066898c1954cfbcc57c0c0493e47b4be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="61777-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="61777-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="61777-103">マッピングの情報ソースへのトークンのスパンの特別なカスタム データ セクションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="61777-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="61777-104">閉じた後は、以上のマッピング情報を追加できます。</span><span class="sxs-lookup"><span data-stu-id="61777-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61777-105">構文</span><span class="sxs-lookup"><span data-stu-id="61777-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="61777-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="61777-106">Return Value</span></span>  
 <span data-ttu-id="61777-107">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="61777-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61777-108">要件</span><span class="sxs-lookup"><span data-stu-id="61777-108">Requirements</span></span>  
 <span data-ttu-id="61777-109">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="61777-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61777-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="61777-110">See Also</span></span>  
 [<span data-ttu-id="61777-111">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61777-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
