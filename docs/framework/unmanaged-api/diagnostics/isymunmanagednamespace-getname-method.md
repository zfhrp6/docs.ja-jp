---
title: ISymUnmanagedNamespace::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aeb3c4e9a1d87b2d93a310b88c340aec0955a845
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425299"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="b66e3-102">ISymUnmanagedNamespace::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="b66e3-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="b66e3-103">この名前空間の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="b66e3-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b66e3-104">構文</span><span class="sxs-lookup"><span data-stu-id="b66e3-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b66e3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b66e3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b66e3-106">[in]A`ULONG32`のサイズを示す、`szName`バッファー。</span><span class="sxs-lookup"><span data-stu-id="b66e3-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b66e3-107">[out]ポインター、`ULONG32`文字、終端の null を含む、名前空間の名前を格納するために必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="b66e3-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="b66e3-108">[out]名前空間の名前を格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b66e3-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b66e3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="b66e3-109">Return Value</span></span>  
 <span data-ttu-id="b66e3-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="b66e3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b66e3-111">要件</span><span class="sxs-lookup"><span data-stu-id="b66e3-111">Requirements</span></span>  
 <span data-ttu-id="b66e3-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b66e3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b66e3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b66e3-113">See Also</span></span>  
 [<span data-ttu-id="b66e3-114">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b66e3-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
