---
title: "ISymUnmanagedDocument::GetLanguageVendor メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetLanguageVendor
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 72fffae9995f44be9a9359c16bb876d79c9a8242
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="de606-102">ISymUnmanagedDocument::GetLanguageVendor メソッド</span><span class="sxs-lookup"><span data-stu-id="de606-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="de606-103">このドキュメントの言語の販売元を取得します。</span><span class="sxs-lookup"><span data-stu-id="de606-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de606-104">構文</span><span class="sxs-lookup"><span data-stu-id="de606-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de606-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de606-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="de606-106">[out]言語の販売元を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="de606-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de606-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="de606-107">Return Value</span></span>  
 <span data-ttu-id="de606-108">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="de606-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de606-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="de606-109">See Also</span></span>  
 [<span data-ttu-id="de606-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de606-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
