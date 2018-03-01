---
title: "ISymUnmanagedWriter2::DefineGlobalVariable2 メソッド"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 617e3f03f4b1c126a56b47db34ec7044bea8c58b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="1097f-102">ISymUnmanagedWriter2::DefineGlobalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="1097f-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="1097f-103">単一のグローバル変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="1097f-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1097f-104">構文</span><span class="sxs-lookup"><span data-stu-id="1097f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1097f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1097f-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1097f-106">[in]グローバル変数の名前。</span><span class="sxs-lookup"><span data-stu-id="1097f-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="1097f-107">[in]グローバル変数の属性。</span><span class="sxs-lookup"><span data-stu-id="1097f-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="1097f-108">[in]署名のメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="1097f-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="1097f-109">[in]アドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="1097f-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="1097f-110">[in]パラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="1097f-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="1097f-111">[in]パラメーター指定の 2 番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="1097f-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="1097f-112">[in]パラメーター指定の 3 番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="1097f-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1097f-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="1097f-113">Return Value</span></span>  
 <span data-ttu-id="1097f-114">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="1097f-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1097f-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="1097f-115">Requirements</span></span>  
 <span data-ttu-id="1097f-116">**ヘッダー:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="1097f-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1097f-117">参照</span><span class="sxs-lookup"><span data-stu-id="1097f-117">See Also</span></span>  
 [<span data-ttu-id="1097f-118">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1097f-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="1097f-119">DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="1097f-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
