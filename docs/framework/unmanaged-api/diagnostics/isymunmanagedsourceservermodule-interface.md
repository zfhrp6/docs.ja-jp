---
title: "ISymUnmanagedSourceServerModule インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSourceServerModule
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSourceServerModule
helpviewer_keywords: ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f183c3ea69de15387f729a67328bf5ea57931750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="b4ae4-102">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4ae4-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="b4ae4-103">モジュールのソース サーバーのデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="b4ae4-103">Provides source server data for a module.</span></span> <span data-ttu-id="b4ae4-104">このインターフェイスを呼び出すことによって取得`QueryInterface`を実装するオブジェクトに対して、 [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b4ae4-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4ae4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b4ae4-105">Methods</span></span>  
  
|<span data-ttu-id="b4ae4-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b4ae4-106">Method</span></span>|<span data-ttu-id="b4ae4-107">説明</span><span class="sxs-lookup"><span data-stu-id="b4ae4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4ae4-108">GetSourceServerData メソッド</span><span class="sxs-lookup"><span data-stu-id="b4ae4-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="b4ae4-109">モジュールのソース サーバーのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="b4ae4-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4ae4-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="b4ae4-110">Requirements</span></span>  
 <span data-ttu-id="b4ae4-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b4ae4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ae4-112">参照</span><span class="sxs-lookup"><span data-stu-id="b4ae4-112">See Also</span></span>  
 [<span data-ttu-id="b4ae4-113">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4ae4-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
