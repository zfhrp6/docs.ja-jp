---
title: ISymUnmanagedDispose インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose
helpviewer_keywords:
- ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 973fc35bb99bea6b3302760763069b9df6c548e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424405"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="dcba1-102">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcba1-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="dcba1-103">アンマネージ リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="dcba1-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcba1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="dcba1-104">Methods</span></span>  
  
|<span data-ttu-id="dcba1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dcba1-105">Method</span></span>|<span data-ttu-id="dcba1-106">説明</span><span class="sxs-lookup"><span data-stu-id="dcba1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dcba1-107">destroy メソッド</span><span class="sxs-lookup"><span data-stu-id="dcba1-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="dcba1-108">により、基になるオブジェクトをすべての内部参照を解放し、後続のメソッド呼び出しでエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="dcba1-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcba1-109">要件</span><span class="sxs-lookup"><span data-stu-id="dcba1-109">Requirements</span></span>  
 <span data-ttu-id="dcba1-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dcba1-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcba1-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcba1-111">See Also</span></span>  
 [<span data-ttu-id="dcba1-112">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcba1-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
