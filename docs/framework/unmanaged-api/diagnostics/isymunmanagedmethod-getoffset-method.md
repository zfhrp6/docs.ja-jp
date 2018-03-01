---
title: "ISymUnmanagedMethod::GetOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c60d35b63d083ce4e23119e3fcb5e64c518f0ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="a9991-102">ISymUnmanagedMethod::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="a9991-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="a9991-103">ドキュメント内の指定位置に対応するこのメソッド内のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="a9991-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9991-104">構文</span><span class="sxs-lookup"><span data-stu-id="a9991-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9991-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9991-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="a9991-106">[in]オフセットを要求する対象のドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a9991-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="a9991-107">[in]オフセットの要求対象となるドキュメント行。</span><span class="sxs-lookup"><span data-stu-id="a9991-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="a9991-108">[in]オフセットの要求対象となるドキュメント列。</span><span class="sxs-lookup"><span data-stu-id="a9991-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a9991-109">[out]ポインター、`ULONG32`オフセットを受け取る。</span><span class="sxs-lookup"><span data-stu-id="a9991-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9991-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a9991-110">Return Value</span></span>  
 <span data-ttu-id="a9991-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="a9991-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9991-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="a9991-112">Requirements</span></span>  
 <span data-ttu-id="a9991-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a9991-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9991-114">参照</span><span class="sxs-lookup"><span data-stu-id="a9991-114">See Also</span></span>  
 [<span data-ttu-id="a9991-115">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a9991-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
