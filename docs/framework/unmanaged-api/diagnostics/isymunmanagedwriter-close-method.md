---
title: ISymUnmanagedWriter::Close メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30747fa25528f5679264ebfb67addf401b7d01d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426330"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="35689-102">ISymUnmanagedWriter::Close メソッド</span><span class="sxs-lookup"><span data-stu-id="35689-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="35689-103">シンボルをシンボル ストアにコミットした後にシンボル ライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="35689-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35689-104">構文</span><span class="sxs-lookup"><span data-stu-id="35689-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="35689-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="35689-105">Return Value</span></span>  
 <span data-ttu-id="35689-106">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="35689-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35689-107">コメント</span><span class="sxs-lookup"><span data-stu-id="35689-107">Remarks</span></span>  
 <span data-ttu-id="35689-108">この呼び出しの後、シンボル ライターが、以降の更新を無効になります。</span><span class="sxs-lookup"><span data-stu-id="35689-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="35689-109">シンボルをコミットすることがなくシンボル ライターを閉じるには使用、 [isymunmanagedwriter::abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="35689-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35689-110">要件</span><span class="sxs-lookup"><span data-stu-id="35689-110">Requirements</span></span>  
 <span data-ttu-id="35689-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="35689-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35689-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="35689-112">See Also</span></span>  
 [<span data-ttu-id="35689-113">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35689-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
