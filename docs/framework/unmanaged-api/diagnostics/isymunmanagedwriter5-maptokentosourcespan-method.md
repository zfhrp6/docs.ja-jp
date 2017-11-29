---
title: "ISymUnmanagedWriter5::MapTokenToSourceSpan メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: adcdf44582aaf801a39c9beb9831c493a9945fd0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="0dab0-102">ISymUnmanagedWriter5::MapTokenToSourceSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="0dab0-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="0dab0-103">マップ指定されたソース行に指定したメタデータ トークンは、指定されたソース ファイルにわたっています。</span><span class="sxs-lookup"><span data-stu-id="0dab0-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="0dab0-104">呼び出しの間で呼び出す必要があります[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="0dab0-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dab0-105">構文</span><span class="sxs-lookup"><span data-stu-id="0dab0-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0dab0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0dab0-106">Parameters</span></span>  
  
|<span data-ttu-id="0dab0-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0dab0-107">Parameter</span></span>|<span data-ttu-id="0dab0-108">説明</span><span class="sxs-lookup"><span data-stu-id="0dab0-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="0dab0-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="0dab0-109">Return Value</span></span>  
 <span data-ttu-id="0dab0-110">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="0dab0-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dab0-111">要件</span><span class="sxs-lookup"><span data-stu-id="0dab0-111">Requirements</span></span>  
 <span data-ttu-id="0dab0-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0dab0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dab0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dab0-113">See Also</span></span>  
 [<span data-ttu-id="0dab0-114">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0dab0-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
