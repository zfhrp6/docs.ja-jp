---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan メソッド
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7751ed951c213c52c68125543622ed110124f5b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427944"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="d2cbd-102">ISymUnmanagedWriter5::MapTokenToSourceSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="d2cbd-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="d2cbd-103">マップ指定されたソース行に指定したメタデータ トークンは、指定されたソース ファイルにわたっています。</span><span class="sxs-lookup"><span data-stu-id="d2cbd-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="d2cbd-104">呼び出しの間で呼び出す必要があります[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="d2cbd-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2cbd-105">構文</span><span class="sxs-lookup"><span data-stu-id="d2cbd-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2cbd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2cbd-106">Parameters</span></span>  
  
|<span data-ttu-id="d2cbd-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2cbd-107">Parameter</span></span>|<span data-ttu-id="d2cbd-108">説明</span><span class="sxs-lookup"><span data-stu-id="d2cbd-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="d2cbd-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d2cbd-109">Return Value</span></span>  
 <span data-ttu-id="d2cbd-110">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="d2cbd-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2cbd-111">要件</span><span class="sxs-lookup"><span data-stu-id="d2cbd-111">Requirements</span></span>  
 <span data-ttu-id="d2cbd-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2cbd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2cbd-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2cbd-113">See Also</span></span>  
 [<span data-ttu-id="d2cbd-114">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2cbd-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
