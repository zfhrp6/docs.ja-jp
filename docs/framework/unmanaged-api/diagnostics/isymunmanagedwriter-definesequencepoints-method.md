---
title: "ISymUnmanagedWriter::DefineSequencePoints メソッド"
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
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e1dcc427a6d034ce108ca66f71cc24b1050a72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="48a9f-102">ISymUnmanagedWriter::DefineSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="48a9f-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="48a9f-103">現在のメソッド内のシーケンス ポイントのグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="48a9f-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="48a9f-104">各開始行と開始列は、メソッド内のステートメントの開始を定義します。</span><span class="sxs-lookup"><span data-stu-id="48a9f-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="48a9f-105">それぞれの終了行と列の終了は、メソッド内のステートメントの末尾を定義します。</span><span class="sxs-lookup"><span data-stu-id="48a9f-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="48a9f-106">配列は、オフセットの昇順に並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="48a9f-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="48a9f-107">オフセットは常に、(バイト単位)、メソッドの先頭から測定されます。</span><span class="sxs-lookup"><span data-stu-id="48a9f-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48a9f-108">構文</span><span class="sxs-lookup"><span data-stu-id="48a9f-108">Syntax</span></span>  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48a9f-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48a9f-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="48a9f-110">[in]シーケンス ポイントが定義されているドキュメント オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="48a9f-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="48a9f-111">[in]A`ULONG32`をそれぞれのサイズを示す、 `offsets`、 `lines`、 `columns`、 `endLines`、および`endColumns`バッファー。</span><span class="sxs-lookup"><span data-stu-id="48a9f-111">[in] A `ULONG32` that that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="48a9f-112">[in]シーケンス ポイントのオフセットは、メソッドの先頭から計測されます。</span><span class="sxs-lookup"><span data-stu-id="48a9f-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="48a9f-113">[in]シーケンス ポイントの開始行番号。</span><span class="sxs-lookup"><span data-stu-id="48a9f-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="48a9f-114">[in]シーケンス ポイントの開始列番号。</span><span class="sxs-lookup"><span data-stu-id="48a9f-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="48a9f-115">[in]シーケンス ポイントの終了行番号。</span><span class="sxs-lookup"><span data-stu-id="48a9f-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="48a9f-116">このパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="48a9f-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="48a9f-117">[in]シーケンス ポイントの終了列番号。</span><span class="sxs-lookup"><span data-stu-id="48a9f-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="48a9f-118">このパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="48a9f-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48a9f-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="48a9f-119">Return Value</span></span>  
 <span data-ttu-id="48a9f-120">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="48a9f-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48a9f-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="48a9f-121">Requirements</span></span>  
 <span data-ttu-id="48a9f-122">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="48a9f-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a9f-123">参照</span><span class="sxs-lookup"><span data-stu-id="48a9f-123">See Also</span></span>  
 [<span data-ttu-id="48a9f-124">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48a9f-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
