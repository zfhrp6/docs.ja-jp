---
title: "ISymUnmanagedWriter5::OpenMapTokensToSourceSpans メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f226a71ac6381c8ca04093beb1d9772d6e6c75e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="f9e98-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="f9e98-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="f9e98-103">マップする span トークンからソース情報を出力するカスタム データを特別なセクションを開きます。</span><span class="sxs-lookup"><span data-stu-id="f9e98-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="f9e98-104">メソッドは既に開かれて、またはその逆の場合、エラーは、このセクションの内容を開いています。</span><span class="sxs-lookup"><span data-stu-id="f9e98-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e98-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9e98-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f9e98-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9e98-106">Return Value</span></span>  
 <span data-ttu-id="f9e98-107">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="f9e98-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e98-108">要件</span><span class="sxs-lookup"><span data-stu-id="f9e98-108">Requirements</span></span>  
 <span data-ttu-id="f9e98-109">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9e98-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e98-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9e98-110">See Also</span></span>  
 [<span data-ttu-id="f9e98-111">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9e98-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
