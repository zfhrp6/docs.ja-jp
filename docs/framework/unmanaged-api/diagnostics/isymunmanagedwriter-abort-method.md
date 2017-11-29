---
title: "ISymUnmanagedWriter::Abort メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Abort
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29dd11972e8db80f36820bba1eb679070d02146e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="f167b-102">ISymUnmanagedWriter::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="f167b-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="f167b-103">シンボルをシンボル ストアにコミットせずシンボル ライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f167b-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="f167b-104">この呼び出しの後、シンボル ライターが、以降の更新を無効になります。</span><span class="sxs-lookup"><span data-stu-id="f167b-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="f167b-105">シンボルをコミットし、シンボル ライターを閉じて、使用、 [isymunmanagedwriter::close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="f167b-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f167b-106">構文</span><span class="sxs-lookup"><span data-stu-id="f167b-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f167b-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="f167b-107">Return Value</span></span>  
 <span data-ttu-id="f167b-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="f167b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f167b-109">要件</span><span class="sxs-lookup"><span data-stu-id="f167b-109">Requirements</span></span>  
 <span data-ttu-id="f167b-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f167b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f167b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f167b-111">See Also</span></span>  
 [<span data-ttu-id="f167b-112">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f167b-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
