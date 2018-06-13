---
title: ISymUnmanagedWriter5 インターフェイス
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fd7c2bd4fae94d1ef5021b558a04b734803b68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430558"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="55f04-102">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55f04-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="55f04-103">ISymUnmanagedWriter5 インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="55f04-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f04-104">構文</span><span class="sxs-lookup"><span data-stu-id="55f04-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="55f04-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="55f04-105">Methods</span></span>  
 <span data-ttu-id="55f04-106">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55f04-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="55f04-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="55f04-107">Method</span></span>|<span data-ttu-id="55f04-108">説明</span><span class="sxs-lookup"><span data-stu-id="55f04-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55f04-109">CloseMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="55f04-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="55f04-110">マッピングの情報ソースへのトークンのスパンの特別なカスタム データ セクションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="55f04-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="55f04-111">閉じた後は、以上のマッピング情報を追加できます。</span><span class="sxs-lookup"><span data-stu-id="55f04-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="55f04-112">MapTokenToSourceSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="55f04-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="55f04-113">マップ指定されたソース行に指定したメタデータ トークンは、指定されたソース ファイルにわたっています。</span><span class="sxs-lookup"><span data-stu-id="55f04-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="55f04-114">呼び出しの間で呼び出す必要があります[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="55f04-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="55f04-115">OpenMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="55f04-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="55f04-116">マップする span トークンからソース情報を出力するカスタム データを特別なセクションを開きます。</span><span class="sxs-lookup"><span data-stu-id="55f04-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="55f04-117">メソッドは既に開かれて、またはその逆の場合、エラーは、このセクションの内容を開いています。</span><span class="sxs-lookup"><span data-stu-id="55f04-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55f04-118">要件</span><span class="sxs-lookup"><span data-stu-id="55f04-118">Requirements</span></span>  
 <span data-ttu-id="55f04-119">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="55f04-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f04-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="55f04-120">See Also</span></span>  
 [<span data-ttu-id="55f04-121">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55f04-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="55f04-122">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55f04-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
