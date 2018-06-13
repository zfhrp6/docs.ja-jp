---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a476d92486d7f2523dfbcc8b25e9c11e26c55f2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425616"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="c5be8-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="c5be8-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="c5be8-103">非同期操作を開始する開始メソッドを設定します。</span><span class="sxs-lookup"><span data-stu-id="c5be8-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5be8-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5be8-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5be8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5be8-105">Parameters</span></span>  
  
|<span data-ttu-id="c5be8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5be8-106">Parameter</span></span>|<span data-ttu-id="c5be8-107">説明</span><span class="sxs-lookup"><span data-stu-id="c5be8-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="c5be8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="c5be8-108">Return Value</span></span>  
 <span data-ttu-id="c5be8-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="c5be8-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5be8-110">要件</span><span class="sxs-lookup"><span data-stu-id="c5be8-110">Requirements</span></span>  
 <span data-ttu-id="c5be8-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c5be8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5be8-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5be8-112">See Also</span></span>  
 [<span data-ttu-id="c5be8-113">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5be8-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
