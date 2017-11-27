---
title: "ISymUnmanagedReader::GetMethodFromDocumentPosition メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad64d5722df68859e7be9d44b94b95cf1f43823f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="03025-102">ISymUnmanagedReader::GetMethodFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="03025-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="03025-103">ドキュメント内の指定位置にブレークポイントを含むメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="03025-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03025-104">構文</span><span class="sxs-lookup"><span data-stu-id="03025-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03025-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03025-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="03025-106">[in]指定されたドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="03025-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="03025-107">[in]指定されたドキュメントの行。</span><span class="sxs-lookup"><span data-stu-id="03025-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="03025-108">[in]指定されたドキュメントの列です。</span><span class="sxs-lookup"><span data-stu-id="03025-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="03025-109">[out]アドレスへのポインター、 [ISymUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)ブレークポイントを含むメソッドを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="03025-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03025-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="03025-110">Return Value</span></span>  
 <span data-ttu-id="03025-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="03025-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03025-112">要件</span><span class="sxs-lookup"><span data-stu-id="03025-112">Requirements</span></span>  
 <span data-ttu-id="03025-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="03025-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03025-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="03025-114">See Also</span></span>  
 [<span data-ttu-id="03025-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03025-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
