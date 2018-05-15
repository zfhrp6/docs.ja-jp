---
title: ISymUnmanagedDocumentWriter::SetCheckSum メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b9b77b94e466a4aab4a575501ac6922293b3410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="24402-102">ISymUnmanagedDocumentWriter::SetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="24402-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="24402-103">チェックサム情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="24402-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24402-104">構文</span><span class="sxs-lookup"><span data-stu-id="24402-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24402-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24402-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="24402-106">[in]アルゴリズム識別子を表す GUID。</span><span class="sxs-lookup"><span data-stu-id="24402-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="24402-107">[in]A`ULONG32`のサイズ (バイト単位) を示す、`checkSum`バッファー。</span><span class="sxs-lookup"><span data-stu-id="24402-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="24402-108">[in]チェックサム情報を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="24402-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24402-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="24402-109">Return Value</span></span>  
 <span data-ttu-id="24402-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="24402-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24402-111">要件</span><span class="sxs-lookup"><span data-stu-id="24402-111">Requirements</span></span>  
 <span data-ttu-id="24402-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="24402-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24402-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="24402-113">See Also</span></span>  
 [<span data-ttu-id="24402-114">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24402-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
