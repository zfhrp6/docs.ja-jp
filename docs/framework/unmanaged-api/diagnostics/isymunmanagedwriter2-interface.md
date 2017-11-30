---
title: "ISymUnmanagedWriter2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2
helpviewer_keywords: ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd297a8ee0172f1624e6983de9bc9bf25bd86621
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="38a47-102">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38a47-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="38a47-103">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="38a47-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="38a47-104">このインターフェイスは、 [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="38a47-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38a47-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="38a47-105">Methods</span></span>  
  
|<span data-ttu-id="38a47-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="38a47-106">Method</span></span>|<span data-ttu-id="38a47-107">説明</span><span class="sxs-lookup"><span data-stu-id="38a47-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38a47-108">DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="38a47-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="38a47-109">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="38a47-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="38a47-110">DefineGlobalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="38a47-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="38a47-111">単一のグローバル変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="38a47-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="38a47-112">DefineLocalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="38a47-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="38a47-113">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="38a47-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38a47-114">要件</span><span class="sxs-lookup"><span data-stu-id="38a47-114">Requirements</span></span>  
 <span data-ttu-id="38a47-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="38a47-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a47-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="38a47-116">See Also</span></span>  
 [<span data-ttu-id="38a47-117">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="38a47-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="38a47-118">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38a47-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="38a47-119">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38a47-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
