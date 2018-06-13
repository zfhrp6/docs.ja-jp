---
title: ISymENCUnmanagedMethod インターフェイス
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 575c732cf1b1caf4700568a9d168463359d1ad7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425504"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="1e043-102">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e043-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="1e043-103">エディット コンティニュ機能についてを説明します。</span><span class="sxs-lookup"><span data-stu-id="1e043-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e043-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1e043-104">Methods</span></span>  
  
|<span data-ttu-id="1e043-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1e043-105">Method</span></span>|<span data-ttu-id="1e043-106">説明</span><span class="sxs-lookup"><span data-stu-id="1e043-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e043-107">GetDocumentsForMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="1e043-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="1e043-108">このメソッドの行が含まれるドキュメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e043-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="1e043-109">GetDocumentsForMethodCount メソッド</span><span class="sxs-lookup"><span data-stu-id="1e043-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="1e043-110">このメソッドの行が含まれるドキュメントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e043-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="1e043-111">GetFileNameFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="1e043-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="1e043-112">オフセットに関連付けられている行のファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e043-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="1e043-113">GetLineFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="1e043-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="1e043-114">オフセットに関連付けられている行の情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e043-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="1e043-115">GetSourceExtentInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="1e043-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="1e043-116">取得では、特定のドキュメントに行と、メソッドの末尾行を最大を最小を開始します。</span><span class="sxs-lookup"><span data-stu-id="1e043-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e043-117">要件</span><span class="sxs-lookup"><span data-stu-id="1e043-117">Requirements</span></span>  
 <span data-ttu-id="1e043-118">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1e043-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e043-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e043-119">See Also</span></span>  
 [<span data-ttu-id="1e043-120">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e043-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
