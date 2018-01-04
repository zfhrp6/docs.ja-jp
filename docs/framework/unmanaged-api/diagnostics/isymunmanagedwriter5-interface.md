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
ms.workload: dotnet
ms.openlocfilehash: 701b8de977d49a7d93f393b320bcb9d0d780c7bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="18289-102">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18289-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="18289-103">ISymUnmanagedWriter5 インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="18289-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18289-104">構文</span><span class="sxs-lookup"><span data-stu-id="18289-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="18289-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="18289-105">Methods</span></span>  
 <span data-ttu-id="18289-106">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="18289-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="18289-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="18289-107">Method</span></span>|<span data-ttu-id="18289-108">説明</span><span class="sxs-lookup"><span data-stu-id="18289-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18289-109">CloseMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="18289-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="18289-110">マッピングの情報ソースへのトークンのスパンの特別なカスタム データ セクションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="18289-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="18289-111">閉じた後は、以上のマッピング情報を追加できます。</span><span class="sxs-lookup"><span data-stu-id="18289-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="18289-112">MapTokenToSourceSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="18289-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="18289-113">マップ指定されたソース行に指定したメタデータ トークンは、指定されたソース ファイルにわたっています。</span><span class="sxs-lookup"><span data-stu-id="18289-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="18289-114">呼び出しの間で呼び出す必要があります[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="18289-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="18289-115">OpenMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="18289-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="18289-116">マップする span トークンからソース情報を出力するカスタム データを特別なセクションを開きます。</span><span class="sxs-lookup"><span data-stu-id="18289-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="18289-117">メソッドは既に開かれて、またはその逆の場合、エラーは、このセクションの内容を開いています。</span><span class="sxs-lookup"><span data-stu-id="18289-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18289-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="18289-118">Requirements</span></span>  
 <span data-ttu-id="18289-119">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="18289-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18289-120">参照</span><span class="sxs-lookup"><span data-stu-id="18289-120">See Also</span></span>  
 [<span data-ttu-id="18289-121">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18289-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="18289-122">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18289-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
