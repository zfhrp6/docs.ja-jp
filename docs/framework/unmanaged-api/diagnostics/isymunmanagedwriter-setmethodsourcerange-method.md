---
title: "ISymUnmanagedWriter::SetMethodSourceRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetMethodSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ed0a73b4862702895e737f2df639b8da7f7679
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="9fa59-102">ISymUnmanagedWriter::SetMethodSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="9fa59-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="9fa59-103">実際の先頭とソース ファイル内のメソッドの末尾を指定します。</span><span class="sxs-lookup"><span data-stu-id="9fa59-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="9fa59-104">このメソッドを使用すると、メソッド内に存在するシーケンス ポイントとは無関係に、メソッドの範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9fa59-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa59-105">構文</span><span class="sxs-lookup"><span data-stu-id="9fa59-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fa59-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9fa59-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="9fa59-107">[in]開始位置を含むドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9fa59-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="9fa59-108">[in]開始行番号。</span><span class="sxs-lookup"><span data-stu-id="9fa59-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="9fa59-109">[in]開始列。</span><span class="sxs-lookup"><span data-stu-id="9fa59-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="9fa59-110">[in]終了位置を含むドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9fa59-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="9fa59-111">[in]終了行番号。</span><span class="sxs-lookup"><span data-stu-id="9fa59-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="9fa59-112">[in]終了列番号。</span><span class="sxs-lookup"><span data-stu-id="9fa59-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fa59-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="9fa59-113">Return Value</span></span>  
 <span data-ttu-id="9fa59-114">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="9fa59-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa59-115">要件</span><span class="sxs-lookup"><span data-stu-id="9fa59-115">Requirements</span></span>  
 <span data-ttu-id="9fa59-116">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9fa59-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa59-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fa59-117">See Also</span></span>  
 [<span data-ttu-id="9fa59-118">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9fa59-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
