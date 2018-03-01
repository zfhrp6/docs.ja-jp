---
title: "ISymUnmanagedWriter2 インターフェイス"
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
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 98461cd2c2bc26d78f3f3f747b95d46576ba01e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="44e43-102">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44e43-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="44e43-103">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="44e43-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="44e43-104">このインターフェイスは、 [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="44e43-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44e43-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="44e43-105">Methods</span></span>  
  
|<span data-ttu-id="44e43-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="44e43-106">Method</span></span>|<span data-ttu-id="44e43-107">説明</span><span class="sxs-lookup"><span data-stu-id="44e43-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44e43-108">DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="44e43-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="44e43-109">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="44e43-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="44e43-110">DefineGlobalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="44e43-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="44e43-111">単一のグローバル変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="44e43-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="44e43-112">DefineLocalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="44e43-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="44e43-113">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="44e43-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44e43-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="44e43-114">Requirements</span></span>  
 <span data-ttu-id="44e43-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="44e43-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e43-116">参照</span><span class="sxs-lookup"><span data-stu-id="44e43-116">See Also</span></span>  
 [<span data-ttu-id="44e43-117">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44e43-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="44e43-118">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44e43-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="44e43-119">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44e43-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
