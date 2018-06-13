---
title: ISymUnmanagedDocument::GetLanguageVendor メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6830f47d5cac2cf9c84144c18486489b0ec581
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424532"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="8af54-102">ISymUnmanagedDocument::GetLanguageVendor メソッド</span><span class="sxs-lookup"><span data-stu-id="8af54-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="8af54-103">このドキュメントの言語の販売元を取得します。</span><span class="sxs-lookup"><span data-stu-id="8af54-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af54-104">構文</span><span class="sxs-lookup"><span data-stu-id="8af54-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8af54-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8af54-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8af54-106">[out]言語の販売元を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8af54-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8af54-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="8af54-107">Return Value</span></span>  
 <span data-ttu-id="8af54-108">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="8af54-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af54-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8af54-109">See Also</span></span>  
 [<span data-ttu-id="8af54-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8af54-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
