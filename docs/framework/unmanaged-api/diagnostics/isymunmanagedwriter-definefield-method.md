---
title: ISymUnmanagedWriter::DefineField メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d5b3c60845fce39ce7f904c6871e7feb16e8970
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429815"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="167f9-102">ISymUnmanagedWriter::DefineField メソッド</span><span class="sxs-lookup"><span data-stu-id="167f9-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="167f9-103">メソッド内ではない 1 つの変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="167f9-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="167f9-104">このメソッドは、使用されるクラス内の特定のフィールド、ビット フィールドです。</span><span class="sxs-lookup"><span data-stu-id="167f9-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="167f9-105">構文</span><span class="sxs-lookup"><span data-stu-id="167f9-105">Syntax</span></span>  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="167f9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="167f9-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="167f9-107">[in]メタデータ型またはメソッド トークンです。</span><span class="sxs-lookup"><span data-stu-id="167f9-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="167f9-108">[in]フィールド名です。</span><span class="sxs-lookup"><span data-stu-id="167f9-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="167f9-109">[in]フィールドの属性。</span><span class="sxs-lookup"><span data-stu-id="167f9-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="167f9-110">[in]A`ULONG32`フィールド シグネチャの格納に必要なバッファーの文字のサイズはします。</span><span class="sxs-lookup"><span data-stu-id="167f9-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="167f9-111">[in]フィールド シグネチャの配列です。</span><span class="sxs-lookup"><span data-stu-id="167f9-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="167f9-112">[in]アドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="167f9-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="167f9-113">[in]フィールド定義の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="167f9-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="167f9-114">[in]フィールド定義の 2 番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="167f9-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="167f9-115">[in]フィールドの仕様の 3 番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="167f9-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="167f9-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="167f9-116">Return Value</span></span>  
 <span data-ttu-id="167f9-117">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="167f9-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="167f9-118">要件</span><span class="sxs-lookup"><span data-stu-id="167f9-118">Requirements</span></span>  
 <span data-ttu-id="167f9-119">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="167f9-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167f9-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="167f9-120">See Also</span></span>  
 [<span data-ttu-id="167f9-121">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="167f9-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
