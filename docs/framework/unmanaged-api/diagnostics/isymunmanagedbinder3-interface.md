---
title: "ISymUnmanagedBinder3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df5cd6d4015fad1baf98909ee9cc923cd9bce05e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="2eca3-102">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2eca3-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="2eca3-103">シンボル バインダー インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="2eca3-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="2eca3-104">このインターフェイスを呼び出すことによって取得`QueryInterface`を実装するオブジェクトに対して、`ISymUnmanagedBinder`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="2eca3-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2eca3-105">信頼できないソースからプログラム データベース (PDB) ファイルを開く、セキュリティ上のリスクを勧めします。</span><span class="sxs-lookup"><span data-stu-id="2eca3-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2eca3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2eca3-106">Methods</span></span>  
  
|<span data-ttu-id="2eca3-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="2eca3-107">Method</span></span>|<span data-ttu-id="2eca3-108">説明</span><span class="sxs-lookup"><span data-stu-id="2eca3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2eca3-109">GetReaderFromCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="2eca3-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="2eca3-110">実装しますまたはコールバックを使用していずれかを指定することができます、`IID_IDiaReadExeAtRVACallback`または`IID_IDiaReadExeAtOffsetCallback`をメモリからデバッグ ディレクトリ情報を取得するには。</span><span class="sxs-lookup"><span data-stu-id="2eca3-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2eca3-111">要件</span><span class="sxs-lookup"><span data-stu-id="2eca3-111">Requirements</span></span>  
 <span data-ttu-id="2eca3-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2eca3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eca3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2eca3-113">See Also</span></span>  
 [<span data-ttu-id="2eca3-114">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="2eca3-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="2eca3-115">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2eca3-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="2eca3-116">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2eca3-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
