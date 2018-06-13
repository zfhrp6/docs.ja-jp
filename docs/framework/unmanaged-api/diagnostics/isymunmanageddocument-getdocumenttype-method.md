---
title: ISymUnmanagedDocument::GetDocumentType メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0460086874af38cad348c965237f8c423f18e868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436001"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="1469e-102">ISymUnmanagedDocument::GetDocumentType メソッド</span><span class="sxs-lookup"><span data-stu-id="1469e-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="1469e-103">このドキュメントのドキュメントの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="1469e-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1469e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1469e-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1469e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1469e-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1469e-106">[out]ドキュメントの種類を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1469e-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1469e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="1469e-107">Return Value</span></span>  
 <span data-ttu-id="1469e-108">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="1469e-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1469e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="1469e-109">See Also</span></span>  
 [<span data-ttu-id="1469e-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1469e-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
