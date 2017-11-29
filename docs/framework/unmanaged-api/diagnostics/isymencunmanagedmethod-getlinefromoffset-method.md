---
title: "ISymENCUnmanagedMethod::GetLineFromOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f18357b3a58a5409da93d4d2491997e9ca1cc70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="99228-102">ISymENCUnmanagedMethod::GetLineFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="99228-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="99228-103">オフセットに関連付けられている行の情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="99228-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="99228-104">場合オフセット パラメーター (`dwOffset`) は、シーケンス ポイントでは、このメソッドは、前のオフセットに関連付けられている行の情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="99228-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99228-105">構文</span><span class="sxs-lookup"><span data-stu-id="99228-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99228-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="99228-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="99228-107">[in]A`ULONG32`オフセットを格納しています。</span><span class="sxs-lookup"><span data-stu-id="99228-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="99228-108">[out]ポインター、`ULONG32`行を受け取る。</span><span class="sxs-lookup"><span data-stu-id="99228-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="99228-109">[out]ポインター、`ULONG32`列を受け取る。</span><span class="sxs-lookup"><span data-stu-id="99228-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="99228-110">[out]ポインター、`ULONG32`の最終行を受け取る。</span><span class="sxs-lookup"><span data-stu-id="99228-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="99228-111">[out]ポインター、`ULONG32`を受け取る最終列。</span><span class="sxs-lookup"><span data-stu-id="99228-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="99228-112">[out]ポインター、`ULONG32`関連付けられたシーケンス ポイントを受け取る。</span><span class="sxs-lookup"><span data-stu-id="99228-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99228-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="99228-113">Return Value</span></span>  
 <span data-ttu-id="99228-114">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="99228-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99228-115">要件</span><span class="sxs-lookup"><span data-stu-id="99228-115">Requirements</span></span>  
 <span data-ttu-id="99228-116">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="99228-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99228-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="99228-117">See Also</span></span>  
 [<span data-ttu-id="99228-118">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99228-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
