---
title: "ISymUnmanagedReaderSymbolSearchInfo インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7f53e45eb321f114483648afc63d2669065a791
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="312b3-102">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="312b3-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="312b3-103">シンボル検索情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="312b3-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="312b3-104">このインターフェイスを呼び出すことによって取得`QueryInterface`を実装するオブジェクトに対して、 [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="312b3-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="312b3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="312b3-105">Methods</span></span>  
  
|<span data-ttu-id="312b3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="312b3-106">Method</span></span>|<span data-ttu-id="312b3-107">説明</span><span class="sxs-lookup"><span data-stu-id="312b3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="312b3-108">GetSymbolSearchInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="312b3-108">GetSymbolSearchInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="312b3-109">シンボル検索情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="312b3-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="312b3-110">GetSymbolSearchInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="312b3-110">GetSymbolSearchInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="312b3-111">シンボル検索情報の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="312b3-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="312b3-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="312b3-112">Requirements</span></span>  
 <span data-ttu-id="312b3-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="312b3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="312b3-114">参照</span><span class="sxs-lookup"><span data-stu-id="312b3-114">See Also</span></span>  
 [<span data-ttu-id="312b3-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="312b3-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
