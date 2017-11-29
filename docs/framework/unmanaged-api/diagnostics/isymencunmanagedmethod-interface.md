---
title: "ISymENCUnmanagedMethod インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod
helpviewer_keywords: ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 68929dc30b029133c73f18c3749f39f014359c0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="02388-102">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02388-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="02388-103">エディット コンティニュ機能についてを説明します。</span><span class="sxs-lookup"><span data-stu-id="02388-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02388-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="02388-104">Methods</span></span>  
  
|<span data-ttu-id="02388-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="02388-105">Method</span></span>|<span data-ttu-id="02388-106">説明</span><span class="sxs-lookup"><span data-stu-id="02388-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02388-107">GetDocumentsForMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="02388-107">GetDocumentsForMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="02388-108">このメソッドの行が含まれるドキュメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="02388-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="02388-109">GetDocumentsForMethodCount メソッド</span><span class="sxs-lookup"><span data-stu-id="02388-109">GetDocumentsForMethodCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="02388-110">このメソッドの行が含まれるドキュメントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="02388-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="02388-111">GetFileNameFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="02388-111">GetFileNameFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="02388-112">オフセットに関連付けられている行のファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="02388-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="02388-113">GetLineFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="02388-113">GetLineFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="02388-114">オフセットに関連付けられている行の情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="02388-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="02388-115">GetSourceExtentInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="02388-115">GetSourceExtentInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="02388-116">取得では、特定のドキュメントに行と、メソッドの末尾行を最大を最小を開始します。</span><span class="sxs-lookup"><span data-stu-id="02388-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02388-117">要件</span><span class="sxs-lookup"><span data-stu-id="02388-117">Requirements</span></span>  
 <span data-ttu-id="02388-118">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="02388-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02388-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="02388-119">See Also</span></span>  
 [<span data-ttu-id="02388-120">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="02388-120">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
