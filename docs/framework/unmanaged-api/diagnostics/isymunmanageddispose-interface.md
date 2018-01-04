---
title: "ISymUnmanagedDispose インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDispose
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDispose
helpviewer_keywords: ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c7431e7c0e40fe631cf525a961f8bc2710e716d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="58bce-102">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58bce-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="58bce-103">アンマネージ リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="58bce-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58bce-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="58bce-104">Methods</span></span>  
  
|<span data-ttu-id="58bce-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="58bce-105">Method</span></span>|<span data-ttu-id="58bce-106">説明</span><span class="sxs-lookup"><span data-stu-id="58bce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58bce-107">destroy メソッド</span><span class="sxs-lookup"><span data-stu-id="58bce-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="58bce-108">により、基になるオブジェクトをすべての内部参照を解放し、後続のメソッド呼び出しでエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="58bce-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58bce-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="58bce-109">Requirements</span></span>  
 <span data-ttu-id="58bce-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="58bce-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58bce-111">参照</span><span class="sxs-lookup"><span data-stu-id="58bce-111">See Also</span></span>  
 [<span data-ttu-id="58bce-112">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58bce-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
