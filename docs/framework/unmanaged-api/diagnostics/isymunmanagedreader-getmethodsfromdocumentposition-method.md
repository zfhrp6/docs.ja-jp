---
title: "ISymUnmanagedReader::GetMethodsFromDocumentPosition メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7f82cf213e9bcc83055cfaa42b9acab9d395d405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="d1ee4-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="d1ee4-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="d1ee4-103">メソッドのドキュメントで指定された位置にブレークポイントを含むそれぞれの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="d1ee4-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ee4-104">構文</span><span class="sxs-lookup"><span data-stu-id="d1ee4-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1ee4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d1ee4-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="d1ee4-106">[in]指定されたドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="d1ee4-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="d1ee4-107">[in]指定されたドキュメントの行。</span><span class="sxs-lookup"><span data-stu-id="d1ee4-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="d1ee4-108">[in]指定されたドキュメントの列です。</span><span class="sxs-lookup"><span data-stu-id="d1ee4-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="d1ee4-109">[in] `pRetVal` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d1ee4-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="d1ee4-110">[out]返される要素の数を受け取る変数へのポインター、`pRetVal`配列。</span><span class="sxs-lookup"><span data-stu-id="d1ee4-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d1ee4-111">[out]それぞれが指すポインターの配列、 [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)ブレークポイントを含むメソッドを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d1ee4-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1ee4-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="d1ee4-112">Return Value</span></span>  
 <span data-ttu-id="d1ee4-113">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="d1ee4-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1ee4-114">要件</span><span class="sxs-lookup"><span data-stu-id="d1ee4-114">Requirements</span></span>  
 <span data-ttu-id="d1ee4-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d1ee4-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ee4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1ee4-116">See Also</span></span>  
 [<span data-ttu-id="d1ee4-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1ee4-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
