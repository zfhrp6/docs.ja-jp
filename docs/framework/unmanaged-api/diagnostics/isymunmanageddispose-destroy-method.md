---
title: "ISymUnmanagedDispose::Destroy メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDispose.Destroy
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d808392d883d1168d6aad8d16ab50ce072b1d9f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="5028d-102">ISymUnmanagedDispose::Destroy メソッド</span><span class="sxs-lookup"><span data-stu-id="5028d-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="5028d-103">により、基になるオブジェクトをすべての内部参照を解放し、後続のメソッド呼び出しでエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="5028d-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5028d-104">構文</span><span class="sxs-lookup"><span data-stu-id="5028d-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5028d-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="5028d-105">Return Value</span></span>  
 <span data-ttu-id="5028d-106">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="5028d-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5028d-107">要件</span><span class="sxs-lookup"><span data-stu-id="5028d-107">Requirements</span></span>  
 <span data-ttu-id="5028d-108">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5028d-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5028d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="5028d-109">See Also</span></span>  
 [<span data-ttu-id="5028d-110">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5028d-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
