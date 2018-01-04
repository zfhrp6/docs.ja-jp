---
title: "ISymUnmanagedReader::GetGlobalVariables メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetGlobalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17abe352dc37b366294e72de53bcc4e1ad8dc9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="5b99d-102">ISymUnmanagedReader::GetGlobalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="5b99d-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="5b99d-103">すべてのグローバル変数を返します。</span><span class="sxs-lookup"><span data-stu-id="5b99d-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b99d-104">構文</span><span class="sxs-lookup"><span data-stu-id="5b99d-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b99d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b99d-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="5b99d-106">[in]バッファーの長さを指す`pcVars`です。</span><span class="sxs-lookup"><span data-stu-id="5b99d-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="5b99d-107">[out]ポインター、`ULONG32`変数の格納に必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="5b99d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="5b99d-108">[out]変数を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="5b99d-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b99d-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5b99d-109">Return Value</span></span>  
 <span data-ttu-id="5b99d-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="5b99d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b99d-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="5b99d-111">Requirements</span></span>  
 <span data-ttu-id="5b99d-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5b99d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b99d-113">参照</span><span class="sxs-lookup"><span data-stu-id="5b99d-113">See Also</span></span>  
 [<span data-ttu-id="5b99d-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5b99d-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
