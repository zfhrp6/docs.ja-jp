---
title: "ISymUnmanagedScope2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope2
helpviewer_keywords: ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5eed6061c8108fcf91f8ac1ac9ff139da426f0e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="514c5-102">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="514c5-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="514c5-103">メソッド内での構文のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="514c5-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="514c5-104">このインターフェイスは、 [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)スコープ内で定義されている定数に関する情報を取得するメソッドを持つインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="514c5-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="514c5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="514c5-105">Methods</span></span>  
  
|<span data-ttu-id="514c5-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="514c5-106">Method</span></span>|<span data-ttu-id="514c5-107">説明</span><span class="sxs-lookup"><span data-stu-id="514c5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="514c5-108">GetConstantCount メソッド</span><span class="sxs-lookup"><span data-stu-id="514c5-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="514c5-109">このスコープ内で定義されている定数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="514c5-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="514c5-110">GetConstants メソッド</span><span class="sxs-lookup"><span data-stu-id="514c5-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="514c5-111">このスコープ内で定義されているローカル定数を取得します。</span><span class="sxs-lookup"><span data-stu-id="514c5-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="514c5-112">要件</span><span class="sxs-lookup"><span data-stu-id="514c5-112">Requirements</span></span>  
 <span data-ttu-id="514c5-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="514c5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="514c5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="514c5-114">See Also</span></span>  
 [<span data-ttu-id="514c5-115">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="514c5-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="514c5-116">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="514c5-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
