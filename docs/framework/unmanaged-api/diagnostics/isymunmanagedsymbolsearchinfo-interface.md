---
title: "ISymUnmanagedSymbolSearchInfo インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo
helpviewer_keywords: ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 441330471906a891646ad55eb73ec25b44800cbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="0c6da-102">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c6da-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="0c6da-103">検索パスに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0c6da-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="0c6da-104">このインターフェイスを呼び出すことによって取得`QueryInterface`を実装するオブジェクトに対して、 [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="0c6da-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c6da-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0c6da-105">Methods</span></span>  
  
|<span data-ttu-id="0c6da-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0c6da-106">Method</span></span>|<span data-ttu-id="0c6da-107">説明</span><span class="sxs-lookup"><span data-stu-id="0c6da-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c6da-108">GetHRESULT メソッド</span><span class="sxs-lookup"><span data-stu-id="0c6da-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="0c6da-109">HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="0c6da-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="0c6da-110">GetSearchPath メソッド</span><span class="sxs-lookup"><span data-stu-id="0c6da-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="0c6da-111">検索パスを取得します。</span><span class="sxs-lookup"><span data-stu-id="0c6da-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="0c6da-112">GetSearchPathLength メソッド</span><span class="sxs-lookup"><span data-stu-id="0c6da-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="0c6da-113">検索パスの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="0c6da-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c6da-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="0c6da-114">Requirements</span></span>  
 <span data-ttu-id="0c6da-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0c6da-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c6da-116">参照</span><span class="sxs-lookup"><span data-stu-id="0c6da-116">See Also</span></span>  
 [<span data-ttu-id="0c6da-117">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c6da-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
