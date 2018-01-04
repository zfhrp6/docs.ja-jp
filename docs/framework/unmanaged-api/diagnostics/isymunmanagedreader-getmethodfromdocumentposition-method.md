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
ms.workload: dotnet
ms.openlocfilehash: 4fa9bfa324254a48d43c4c3df5ecebb91b3f0ae1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="10b9f-102">ISymUnmanagedReader::GetMethodFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="10b9f-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="10b9f-103">ドキュメント内の指定位置にブレークポイントを含むメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="10b9f-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10b9f-104">構文</span><span class="sxs-lookup"><span data-stu-id="10b9f-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10b9f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10b9f-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="10b9f-106">[in]指定されたドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="10b9f-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="10b9f-107">[in]指定されたドキュメントの行。</span><span class="sxs-lookup"><span data-stu-id="10b9f-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="10b9f-108">[in]指定されたドキュメントの列です。</span><span class="sxs-lookup"><span data-stu-id="10b9f-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="10b9f-109">[out]アドレスへのポインター、 [ISymUnmanagedMethod インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)ブレークポイントを含むメソッドを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="10b9f-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10b9f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="10b9f-110">Return Value</span></span>  
 <span data-ttu-id="10b9f-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="10b9f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10b9f-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="10b9f-112">Requirements</span></span>  
 <span data-ttu-id="10b9f-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="10b9f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10b9f-114">参照</span><span class="sxs-lookup"><span data-stu-id="10b9f-114">See Also</span></span>  
 [<span data-ttu-id="10b9f-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10b9f-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
