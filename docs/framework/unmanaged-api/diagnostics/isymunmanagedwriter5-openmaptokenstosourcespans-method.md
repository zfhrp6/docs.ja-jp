---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans メソッド
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d3bc8b00b568f96cd55b7811f310d34c1ff700d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428649"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="a57a7-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="a57a7-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="a57a7-103">マップする span トークンからソース情報を出力するカスタム データを特別なセクションを開きます。</span><span class="sxs-lookup"><span data-stu-id="a57a7-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="a57a7-104">メソッドは既に開かれて、またはその逆の場合、エラーは、このセクションの内容を開いています。</span><span class="sxs-lookup"><span data-stu-id="a57a7-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a57a7-105">構文</span><span class="sxs-lookup"><span data-stu-id="a57a7-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a57a7-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="a57a7-106">Return Value</span></span>  
 <span data-ttu-id="a57a7-107">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="a57a7-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a57a7-108">要件</span><span class="sxs-lookup"><span data-stu-id="a57a7-108">Requirements</span></span>  
 <span data-ttu-id="a57a7-109">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a57a7-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a57a7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="a57a7-110">See Also</span></span>  
 [<span data-ttu-id="a57a7-111">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a57a7-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
