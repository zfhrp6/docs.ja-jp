---
title: "ISymUnmanagedWriter3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3
helpviewer_keywords: ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49928044bcf2c598cdc0e4315d569f2c4eb02f1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="dde5e-102">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dde5e-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="dde5e-103">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="dde5e-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="dde5e-104">このインターフェイスは、 [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="dde5e-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dde5e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dde5e-105">Methods</span></span>  
  
|<span data-ttu-id="dde5e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="dde5e-106">Method</span></span>|<span data-ttu-id="dde5e-107">説明</span><span class="sxs-lookup"><span data-stu-id="dde5e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dde5e-108">Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="dde5e-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="dde5e-109">ストリームにこれまでに書き込まれた変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="dde5e-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="dde5e-110">OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="dde5e-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="dde5e-111">メソッドを表示し、イメージ内の実際のセクションのオフセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="dde5e-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dde5e-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="dde5e-112">Requirements</span></span>  
 <span data-ttu-id="dde5e-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dde5e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde5e-114">参照</span><span class="sxs-lookup"><span data-stu-id="dde5e-114">See Also</span></span>  
 [<span data-ttu-id="dde5e-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dde5e-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="dde5e-116">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dde5e-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="dde5e-117">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dde5e-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
