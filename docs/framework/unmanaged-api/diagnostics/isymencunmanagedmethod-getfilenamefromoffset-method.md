---
title: "ISymENCUnmanagedMethod::GetFileNameFromOffset メソッド"
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
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f4b760f2782cf75cf0ab0879eb77e185a93b8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="ab1d3-102">ISymENCUnmanagedMethod::GetFileNameFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="ab1d3-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="ab1d3-103">オフセットに関連付けられている行のファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="ab1d3-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab1d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab1d3-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab1d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab1d3-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="ab1d3-106">[in]A`ULONG32`オフセットを格納しています。</span><span class="sxs-lookup"><span data-stu-id="ab1d3-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ab1d3-107">[in]A`ULONG32`のサイズを示す、`szName`バッファー。</span><span class="sxs-lookup"><span data-stu-id="ab1d3-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ab1d3-108">[out]ポインター、`ULONG32`ファイル名の格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="ab1d3-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="ab1d3-109">[out]ファイル名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="ab1d3-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab1d3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="ab1d3-110">Return Value</span></span>  
 <span data-ttu-id="ab1d3-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ab1d3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab1d3-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="ab1d3-112">Requirements</span></span>  
 <span data-ttu-id="ab1d3-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ab1d3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1d3-114">参照</span><span class="sxs-lookup"><span data-stu-id="ab1d3-114">See Also</span></span>  
 [<span data-ttu-id="ab1d3-115">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab1d3-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
