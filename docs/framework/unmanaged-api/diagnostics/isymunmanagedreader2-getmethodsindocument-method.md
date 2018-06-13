---
title: ISymUnmanagedReader2::GetMethodsInDocument メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 762649e260817c43291de416d2f1a92a8f03afb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427370"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="5bb58-102">ISymUnmanagedReader2::GetMethodsInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="5bb58-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="5bb58-103">指定のドキュメントに行情報を持つすべてのメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="5bb58-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bb58-104">構文</span><span class="sxs-lookup"><span data-stu-id="5bb58-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5bb58-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5bb58-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="5bb58-106">[in]ドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5bb58-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="5bb58-107">[in]A`ULONG32`のサイズを示す、`pRetVal`配列。</span><span class="sxs-lookup"><span data-stu-id="5bb58-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="5bb58-108">[out]ポインター、`ULONG32`メソッドの格納に必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="5bb58-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5bb58-109">[out]メソッドを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5bb58-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bb58-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="5bb58-110">Return Value</span></span>  
 <span data-ttu-id="5bb58-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="5bb58-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bb58-112">要件</span><span class="sxs-lookup"><span data-stu-id="5bb58-112">Requirements</span></span>  
 <span data-ttu-id="5bb58-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5bb58-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb58-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bb58-114">See Also</span></span>  
 [<span data-ttu-id="5bb58-115">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bb58-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
