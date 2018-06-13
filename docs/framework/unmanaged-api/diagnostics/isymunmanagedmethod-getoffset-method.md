---
title: ISymUnmanagedMethod::GetOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d88e9279f70c36fd8a9c626972e33305cded5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424392"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="0987c-102">ISymUnmanagedMethod::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="0987c-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="0987c-103">ドキュメント内の指定位置に対応するこのメソッド内のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="0987c-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0987c-104">構文</span><span class="sxs-lookup"><span data-stu-id="0987c-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0987c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0987c-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="0987c-106">[in]オフセットを要求する対象のドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0987c-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="0987c-107">[in]オフセットの要求対象となるドキュメント行。</span><span class="sxs-lookup"><span data-stu-id="0987c-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="0987c-108">[in]オフセットの要求対象となるドキュメント列。</span><span class="sxs-lookup"><span data-stu-id="0987c-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="0987c-109">[out]ポインター、`ULONG32`オフセットを受け取る。</span><span class="sxs-lookup"><span data-stu-id="0987c-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0987c-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="0987c-110">Return Value</span></span>  
 <span data-ttu-id="0987c-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="0987c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0987c-112">要件</span><span class="sxs-lookup"><span data-stu-id="0987c-112">Requirements</span></span>  
 <span data-ttu-id="0987c-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0987c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0987c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0987c-114">See Also</span></span>  
 [<span data-ttu-id="0987c-115">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0987c-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
