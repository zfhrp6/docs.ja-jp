---
title: ISymUnmanagedDocument::HasEmbeddedSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 350aecb9f9c99c9aa44ae6df6d31c7cb69ae5760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430346"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="42874-102">ISymUnmanagedDocument::HasEmbeddedSource メソッド</span><span class="sxs-lookup"><span data-stu-id="42874-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="42874-103">返します`true`場合は、ドキュメントには、デバッグ シンボルに埋め込まれたソースを返しますそれ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="42874-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42874-104">構文</span><span class="sxs-lookup"><span data-stu-id="42874-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42874-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42874-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="42874-106">[out]ドキュメントがソースになっているかどうかを示す変数へのポインターは、デバッグ シンボルに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="42874-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42874-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="42874-107">Return Value</span></span>  
 <span data-ttu-id="42874-108">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="42874-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42874-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="42874-109">See Also</span></span>  
 [<span data-ttu-id="42874-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42874-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
