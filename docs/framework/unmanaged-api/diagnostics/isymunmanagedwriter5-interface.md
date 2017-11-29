---
title: "ISymUnmanagedWriter5 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c5ac543ad98cc14382f0fb6d0d04fafa7136136e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="ce26c-102">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce26c-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="ce26c-103">ISymUnmanagedWriter5 インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="ce26c-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce26c-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce26c-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="ce26c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ce26c-105">Methods</span></span>  
 <span data-ttu-id="ce26c-106">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ce26c-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="ce26c-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="ce26c-107">Method</span></span>|<span data-ttu-id="ce26c-108">説明</span><span class="sxs-lookup"><span data-stu-id="ce26c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce26c-109">CloseMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="ce26c-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="ce26c-110">マッピングの情報ソースへのトークンのスパンの特別なカスタム データ セクションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ce26c-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="ce26c-111">閉じた後は、以上のマッピング情報を追加できます。</span><span class="sxs-lookup"><span data-stu-id="ce26c-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="ce26c-112">MapTokenToSourceSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="ce26c-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="ce26c-113">マップ指定されたソース行に指定したメタデータ トークンは、指定されたソース ファイルにわたっています。</span><span class="sxs-lookup"><span data-stu-id="ce26c-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="ce26c-114">呼び出しの間で呼び出す必要があります[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="ce26c-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="ce26c-115">OpenMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="ce26c-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="ce26c-116">マップする span トークンからソース情報を出力するカスタム データを特別なセクションを開きます。</span><span class="sxs-lookup"><span data-stu-id="ce26c-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="ce26c-117">メソッドは既に開かれて、またはその逆の場合、エラーは、このセクションの内容を開いています。</span><span class="sxs-lookup"><span data-stu-id="ce26c-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce26c-118">要件</span><span class="sxs-lookup"><span data-stu-id="ce26c-118">Requirements</span></span>  
 <span data-ttu-id="ce26c-119">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ce26c-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce26c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce26c-120">See Also</span></span>  
 [<span data-ttu-id="ce26c-121">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="ce26c-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="ce26c-122">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce26c-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
