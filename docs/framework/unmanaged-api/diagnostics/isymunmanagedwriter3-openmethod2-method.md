---
title: ISymUnmanagedWriter3::OpenMethod2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 643666df9f93d1aa5e09579359ae0db87908f10b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428334"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="4f2cb-102">ISymUnmanagedWriter3::OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="4f2cb-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="4f2cb-103">メソッドを表示し、イメージ内の実際のセクションのオフセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="4f2cb-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f2cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="4f2cb-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f2cb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f2cb-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="4f2cb-106">[in]開かれるメソッドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="4f2cb-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="4f2cb-107">[in]イメージ内のセクションでオフセットします。</span><span class="sxs-lookup"><span data-stu-id="4f2cb-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="4f2cb-108">[in]イメージ内のオフセット。</span><span class="sxs-lookup"><span data-stu-id="4f2cb-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f2cb-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="4f2cb-109">Return Value</span></span>  
 <span data-ttu-id="4f2cb-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="4f2cb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f2cb-111">要件</span><span class="sxs-lookup"><span data-stu-id="4f2cb-111">Requirements</span></span>  
 <span data-ttu-id="4f2cb-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4f2cb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2cb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f2cb-113">See Also</span></span>  
 [<span data-ttu-id="4f2cb-114">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f2cb-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="4f2cb-115">OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="4f2cb-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
