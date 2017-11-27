---
title: "ISymUnmanagedWriter::CloseNamespace メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8423e21fbc868e4b6891279d19b2be7c1faef583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="3a663-102">ISymUnmanagedWriter::CloseNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="3a663-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="3a663-103">終了では、名前空間、最も最近開いたします。</span><span class="sxs-lookup"><span data-stu-id="3a663-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a663-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a663-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3a663-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="3a663-105">Return Value</span></span>  
 <span data-ttu-id="3a663-106">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="3a663-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a663-107">要件</span><span class="sxs-lookup"><span data-stu-id="3a663-107">Requirements</span></span>  
 <span data-ttu-id="3a663-108">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3a663-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a663-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a663-109">See Also</span></span>  
 [<span data-ttu-id="3a663-110">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a663-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="3a663-111">OpenNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="3a663-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
