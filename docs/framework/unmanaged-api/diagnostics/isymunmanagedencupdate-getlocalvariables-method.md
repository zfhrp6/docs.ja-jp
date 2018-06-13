---
title: ISymUnmanagedENCUpdate::GetLocalVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82e657e91e586d7fe409646ea4fb8946c026e84c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424340"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="20c27-102">ISymUnmanagedENCUpdate::GetLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="20c27-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="20c27-103">ローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="20c27-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c27-104">構文</span><span class="sxs-lookup"><span data-stu-id="20c27-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20c27-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20c27-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="20c27-106">[in]メソッドのメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="20c27-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="20c27-107">[in]A`ULONG`のサイズを示す、`rgLocals`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="20c27-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="20c27-108">[out]返される配列の<!--zz<xref:ISymUnmanagedVariable>-->`ISymUnmanagedVariable`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="20c27-108">[out] The returned array of <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable`  instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="20c27-109">[out]ポインター、`ULONG`のサイズを受け取る、`rgLocals`バッファーは、ローカル変数を含めるために必要です。</span><span class="sxs-lookup"><span data-stu-id="20c27-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20c27-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="20c27-110">Return Value</span></span>  
 <span data-ttu-id="20c27-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="20c27-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20c27-112">要件</span><span class="sxs-lookup"><span data-stu-id="20c27-112">Requirements</span></span>  
 <span data-ttu-id="20c27-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="20c27-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c27-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="20c27-114">See Also</span></span>  
 [<span data-ttu-id="20c27-115">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20c27-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
