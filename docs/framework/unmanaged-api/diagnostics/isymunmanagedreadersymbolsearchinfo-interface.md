---
title: ISymUnmanagedReaderSymbolSearchInfo インターフェイス
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e2a0352f52bd617738e6d7cfe33b4d7acdb6da0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427659"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="0b92b-102">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b92b-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>
<span data-ttu-id="0b92b-103">シンボル検索情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0b92b-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="0b92b-104">このインターフェイスを呼び出すことによって取得`QueryInterface`を実装するオブジェクトに対して、 [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="0b92b-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b92b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0b92b-105">Methods</span></span>  
  
|<span data-ttu-id="0b92b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0b92b-106">Method</span></span>|<span data-ttu-id="0b92b-107">説明</span><span class="sxs-lookup"><span data-stu-id="0b92b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b92b-108">GetSymbolSearchInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="0b92b-108">GetSymbolSearchInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="0b92b-109">シンボル検索情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="0b92b-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="0b92b-110">GetSymbolSearchInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="0b92b-110">GetSymbolSearchInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="0b92b-111">シンボル検索情報の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="0b92b-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b92b-112">要件</span><span class="sxs-lookup"><span data-stu-id="0b92b-112">Requirements</span></span>  
 <span data-ttu-id="0b92b-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0b92b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b92b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b92b-114">See Also</span></span>  
 [<span data-ttu-id="0b92b-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b92b-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
