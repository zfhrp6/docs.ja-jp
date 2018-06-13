---
title: ISymUnmanagedWriter::Abort メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb6a3e65b1f1d59cde3bff99e491bcf09816c8ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428059"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="71700-102">ISymUnmanagedWriter::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="71700-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="71700-103">シンボルをシンボル ストアにコミットせずシンボル ライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="71700-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="71700-104">この呼び出しの後、シンボル ライターが、以降の更新を無効になります。</span><span class="sxs-lookup"><span data-stu-id="71700-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="71700-105">シンボルをコミットし、シンボル ライターを閉じて、使用、 [isymunmanagedwriter::close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="71700-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71700-106">構文</span><span class="sxs-lookup"><span data-stu-id="71700-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="71700-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="71700-107">Return Value</span></span>  
 <span data-ttu-id="71700-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="71700-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71700-109">要件</span><span class="sxs-lookup"><span data-stu-id="71700-109">Requirements</span></span>  
 <span data-ttu-id="71700-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="71700-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71700-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="71700-111">See Also</span></span>  
 [<span data-ttu-id="71700-112">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71700-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
