---
title: ISymUnmanagedWriter2::DefineGlobalVariable2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f35e3c9327a3945e6ddce85be52b757294b39aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429725"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="0128d-102">ISymUnmanagedWriter2::DefineGlobalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0128d-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="0128d-103">単一のグローバル変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="0128d-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0128d-104">構文</span><span class="sxs-lookup"><span data-stu-id="0128d-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0128d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0128d-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="0128d-106">[in]グローバル変数の名前。</span><span class="sxs-lookup"><span data-stu-id="0128d-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="0128d-107">[in]グローバル変数の属性。</span><span class="sxs-lookup"><span data-stu-id="0128d-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="0128d-108">[in]署名のメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="0128d-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="0128d-109">[in]アドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="0128d-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="0128d-110">[in]パラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="0128d-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="0128d-111">[in]パラメーター指定の 2 番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="0128d-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="0128d-112">[in]パラメーター指定の 3 番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="0128d-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0128d-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="0128d-113">Return Value</span></span>  
 <span data-ttu-id="0128d-114">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="0128d-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0128d-115">要件</span><span class="sxs-lookup"><span data-stu-id="0128d-115">Requirements</span></span>  
 <span data-ttu-id="0128d-116">**ヘッダー:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="0128d-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0128d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0128d-117">See Also</span></span>  
 [<span data-ttu-id="0128d-118">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0128d-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="0128d-119">DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="0128d-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
