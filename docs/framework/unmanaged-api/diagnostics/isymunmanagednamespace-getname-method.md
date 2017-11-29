---
title: "ISymUnmanagedNamespace::GetName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: abb21c7d5f239b19396d3182b97d9502cfa3da15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="b9112-102">ISymUnmanagedNamespace::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="b9112-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="b9112-103">この名前空間の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9112-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9112-104">構文</span><span class="sxs-lookup"><span data-stu-id="b9112-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9112-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9112-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b9112-106">[in]A`ULONG32`のサイズを示す、`szName`バッファー。</span><span class="sxs-lookup"><span data-stu-id="b9112-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b9112-107">[out]ポインター、`ULONG32`文字、終端の null を含む、名前空間の名前を格納するために必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="b9112-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="b9112-108">[out]名前空間の名前を格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b9112-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9112-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="b9112-109">Return Value</span></span>  
 <span data-ttu-id="b9112-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="b9112-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9112-111">要件</span><span class="sxs-lookup"><span data-stu-id="b9112-111">Requirements</span></span>  
 <span data-ttu-id="b9112-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b9112-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9112-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9112-113">See Also</span></span>  
 [<span data-ttu-id="b9112-114">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9112-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
