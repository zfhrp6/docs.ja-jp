---
title: ISymUnmanagedScope::GetEndOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d13006bc5c09ed065ae1671ee75cf8dce066669d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426304"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="fa39e-102">ISymUnmanagedScope::GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="fa39e-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="fa39e-103">このスコープの終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="fa39e-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa39e-104">構文</span><span class="sxs-lookup"><span data-stu-id="fa39e-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa39e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fa39e-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fa39e-106">[out]ポインター、`ULONG32`を受け取る、終了オフセット。</span><span class="sxs-lookup"><span data-stu-id="fa39e-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa39e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="fa39e-107">Return Value</span></span>  
 <span data-ttu-id="fa39e-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="fa39e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa39e-109">要件</span><span class="sxs-lookup"><span data-stu-id="fa39e-109">Requirements</span></span>  
 <span data-ttu-id="fa39e-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fa39e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa39e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa39e-111">See Also</span></span>  
 [<span data-ttu-id="fa39e-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fa39e-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="fa39e-113">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="fa39e-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
