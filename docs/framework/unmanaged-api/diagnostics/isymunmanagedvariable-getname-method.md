---
title: ISymUnmanagedVariable::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9abbfa14777c5a5f5a77fa91db0fbafee095ba9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="0fec8-102">ISymUnmanagedVariable::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="0fec8-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="0fec8-103">この変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="0fec8-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fec8-104">構文</span><span class="sxs-lookup"><span data-stu-id="0fec8-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fec8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0fec8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0fec8-106">[in]バッファーの長さを`pcchName`パラメーターをポイントします。</span><span class="sxs-lookup"><span data-stu-id="0fec8-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0fec8-107">[out]ポインター、`ULONG32`文字、終端の null を含む、名前を格納するために必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="0fec8-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="0fec8-108">[out]名前を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="0fec8-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fec8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="0fec8-109">Return Value</span></span>  
 <span data-ttu-id="0fec8-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="0fec8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fec8-111">要件</span><span class="sxs-lookup"><span data-stu-id="0fec8-111">Requirements</span></span>  
 <span data-ttu-id="0fec8-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0fec8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fec8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fec8-113">See Also</span></span>  
 [<span data-ttu-id="0fec8-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0fec8-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
