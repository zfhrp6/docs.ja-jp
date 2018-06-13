---
title: ISymUnmanagedWriter3 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1315d54e93769772772d536e9688c754a96c67c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429395"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="4940b-102">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4940b-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="4940b-103">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4940b-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="4940b-104">このインターフェイスは、 [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="4940b-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4940b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4940b-105">Methods</span></span>  
  
|<span data-ttu-id="4940b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="4940b-106">Method</span></span>|<span data-ttu-id="4940b-107">説明</span><span class="sxs-lookup"><span data-stu-id="4940b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4940b-108">Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="4940b-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="4940b-109">ストリームにこれまでに書き込まれた変更をコミットします。</span><span class="sxs-lookup"><span data-stu-id="4940b-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="4940b-110">OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="4940b-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="4940b-111">メソッドを表示し、イメージ内の実際のセクションのオフセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="4940b-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4940b-112">要件</span><span class="sxs-lookup"><span data-stu-id="4940b-112">Requirements</span></span>  
 <span data-ttu-id="4940b-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4940b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4940b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4940b-114">See Also</span></span>  
 [<span data-ttu-id="4940b-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4940b-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="4940b-116">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4940b-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="4940b-117">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4940b-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
