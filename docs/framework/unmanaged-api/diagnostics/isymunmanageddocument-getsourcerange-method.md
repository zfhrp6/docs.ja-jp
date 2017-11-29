---
title: "ISymUnmanagedDocument::GetSourceRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6c47f1f491b184e9abe9d56d0729100b0d9b36a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="78fb2-102">ISymUnmanagedDocument::GetSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="78fb2-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="78fb2-103">指定されたバッファーに埋め込まれたソースの指定した範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="78fb2-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="78fb2-104">バッファーは、ソースを保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="78fb2-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78fb2-105">構文</span><span class="sxs-lookup"><span data-stu-id="78fb2-105">Syntax</span></span>  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78fb2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78fb2-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="78fb2-107">[in]現在のドキュメント内の開始行。</span><span class="sxs-lookup"><span data-stu-id="78fb2-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="78fb2-108">[in]現在のドキュメント内の開始列。</span><span class="sxs-lookup"><span data-stu-id="78fb2-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="78fb2-109">[in]現在のドキュメント内の最終行。</span><span class="sxs-lookup"><span data-stu-id="78fb2-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="78fb2-110">[in]現在のドキュメント内の最終列。</span><span class="sxs-lookup"><span data-stu-id="78fb2-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="78fb2-111">[in](バイト単位)、ソースのサイズ。</span><span class="sxs-lookup"><span data-stu-id="78fb2-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="78fb2-112">[out]ソースのサイズを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="78fb2-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="78fb2-113">[out]サイズ (バイト単位)、ソース ドキュメントの指定された範囲の長さ。</span><span class="sxs-lookup"><span data-stu-id="78fb2-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78fb2-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="78fb2-114">Return Value</span></span>  
 <span data-ttu-id="78fb2-115">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="78fb2-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78fb2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="78fb2-116">See Also</span></span>  
 [<span data-ttu-id="78fb2-117">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="78fb2-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
