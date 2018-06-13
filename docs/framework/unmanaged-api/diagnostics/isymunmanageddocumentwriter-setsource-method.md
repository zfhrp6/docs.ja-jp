---
title: ISymUnmanagedDocumentWriter::SetSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f25f66d7092c50247e24051280eaa7b714297c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424418"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="20311-102">ISymUnmanagedDocumentWriter::SetSource メソッド</span><span class="sxs-lookup"><span data-stu-id="20311-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="20311-103">セットには、書き込まれるドキュメントのソースが埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="20311-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20311-104">構文</span><span class="sxs-lookup"><span data-stu-id="20311-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20311-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20311-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="20311-106">[in]A`ULONG32`のサイズを格納する、`source`バッファー。</span><span class="sxs-lookup"><span data-stu-id="20311-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="20311-107">[in]埋め込まれたソースを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="20311-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20311-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="20311-108">Return Value</span></span>  
 <span data-ttu-id="20311-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="20311-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20311-110">要件</span><span class="sxs-lookup"><span data-stu-id="20311-110">Requirements</span></span>  
 <span data-ttu-id="20311-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="20311-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20311-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="20311-112">See Also</span></span>  
 [<span data-ttu-id="20311-113">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20311-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
