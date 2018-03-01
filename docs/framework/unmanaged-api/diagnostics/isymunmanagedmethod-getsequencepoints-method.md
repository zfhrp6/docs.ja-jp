---
title: "ISymUnmanagedMethod::GetSequencePoints メソッド"
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
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 071cbb6c33b56cb4fb409ab634a89f589db5bab8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="f3044-102">ISymUnmanagedMethod::GetSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="f3044-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="f3044-103">このメソッド内のすべてのシーケンス ポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="f3044-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3044-104">構文</span><span class="sxs-lookup"><span data-stu-id="f3044-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3044-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3044-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="f3044-106">[in]A`ULONG32`のサイズを受け取る、 `offsets`、 `documents`、 `lines`、 `columns`、 `endLines`、および`endColumns`配列。</span><span class="sxs-lookup"><span data-stu-id="f3044-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="f3044-107">[out]ポインター、`ULONG32`シーケンス ポイントの格納に必要なバッファーの長さを受け取る。</span><span class="sxs-lookup"><span data-stu-id="f3044-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="f3044-108">[in]シーケンス ポイントのメソッドの先頭から language (MSIL) オフセットを中級者向けの Microsoft を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="f3044-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="f3044-109">[in]シーケンス ポイントが存在するドキュメントを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="f3044-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="f3044-110">[in]シーケンス ポイントが存在するドキュメントの行を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="f3044-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="f3044-111">[in]シーケンス ポイントが存在するドキュメント内の列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="f3044-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="f3044-112">[in]シーケンス ポイントが終了するドキュメント内の行の配列。</span><span class="sxs-lookup"><span data-stu-id="f3044-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="f3044-113">[in]シーケンス ポイントが終了するドキュメント内の列の配列。</span><span class="sxs-lookup"><span data-stu-id="f3044-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3044-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="f3044-114">Return Value</span></span>  
 <span data-ttu-id="f3044-115">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="f3044-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3044-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="f3044-116">Requirements</span></span>  
 <span data-ttu-id="f3044-117">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f3044-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3044-118">参照</span><span class="sxs-lookup"><span data-stu-id="f3044-118">See Also</span></span>  
 [<span data-ttu-id="f3044-119">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3044-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
