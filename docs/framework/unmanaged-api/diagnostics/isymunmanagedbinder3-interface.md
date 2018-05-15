---
title: ISymUnmanagedBinder3 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06a4d5b1b108c15fa7ee4a7f5270b73f7adc1e6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="178f3-102">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="178f3-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="178f3-103">シンボル バインダー インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="178f3-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="178f3-104">このインターフェイスを呼び出すことによって取得`QueryInterface`を実装するオブジェクトに対して、`ISymUnmanagedBinder`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="178f3-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="178f3-105">信頼できないソースからプログラム データベース (PDB) ファイルを開く、セキュリティ上のリスクを勧めします。</span><span class="sxs-lookup"><span data-stu-id="178f3-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="178f3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="178f3-106">Methods</span></span>  
  
|<span data-ttu-id="178f3-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="178f3-107">Method</span></span>|<span data-ttu-id="178f3-108">説明</span><span class="sxs-lookup"><span data-stu-id="178f3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="178f3-109">GetReaderFromCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="178f3-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="178f3-110">実装しますまたはコールバックを使用していずれかを指定することができます、`IID_IDiaReadExeAtRVACallback`または`IID_IDiaReadExeAtOffsetCallback`をメモリからデバッグ ディレクトリ情報を取得するには。</span><span class="sxs-lookup"><span data-stu-id="178f3-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="178f3-111">要件</span><span class="sxs-lookup"><span data-stu-id="178f3-111">Requirements</span></span>  
 <span data-ttu-id="178f3-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="178f3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="178f3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="178f3-113">See Also</span></span>  
 [<span data-ttu-id="178f3-114">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="178f3-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="178f3-115">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="178f3-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="178f3-116">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="178f3-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
