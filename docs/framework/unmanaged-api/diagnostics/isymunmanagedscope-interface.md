---
title: "ISymUnmanagedScope インターフェイス"
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
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e4d4c83b754945c126913a9d96db47966959fed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="f1acc-102">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1acc-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="f1acc-103">メソッド内での構文のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1acc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-104">Methods</span></span>  
  
|<span data-ttu-id="f1acc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-105">Method</span></span>|<span data-ttu-id="f1acc-106">説明</span><span class="sxs-lookup"><span data-stu-id="f1acc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1acc-107">GetChildren メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="f1acc-108">このスコープの子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="f1acc-109">GetEndOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="f1acc-110">このスコープの終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="f1acc-111">GetLocalCount メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="f1acc-112">このスコープ内で定義されているローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="f1acc-113">GetLocals メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="f1acc-114">このスコープ内で定義されているローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="f1acc-115">GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="f1acc-116">このスコープに含まれているメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="f1acc-117">GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="f1acc-118">このスコープ内で使用されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="f1acc-119">GetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="f1acc-120">このスコープの親スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="f1acc-121">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="f1acc-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="f1acc-122">このスコープの開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="f1acc-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1acc-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="f1acc-123">Requirements</span></span>  
 <span data-ttu-id="f1acc-124">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f1acc-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1acc-125">参照</span><span class="sxs-lookup"><span data-stu-id="f1acc-125">See Also</span></span>  
 [<span data-ttu-id="f1acc-126">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1acc-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="f1acc-127">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1acc-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
