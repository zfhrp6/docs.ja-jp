---
title: ICorDebugObjectValue2::GetVirtualMethodAndType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9a6978f35b5ea9fb71f8e933dbc7a08b1c390ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416502"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="841a3-102">ICorDebugObjectValue2::GetVirtualMethodAndType メソッド</span><span class="sxs-lookup"><span data-stu-id="841a3-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="841a3-103">このメソッドはまだ実装されていません。</span><span class="sxs-lookup"><span data-stu-id="841a3-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="841a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="841a3-104">Syntax</span></span>  
  
```  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="841a3-105">コメント</span><span class="sxs-lookup"><span data-stu-id="841a3-105">Remarks</span></span>  
 <span data-ttu-id="841a3-106">取得、最派生方法と、指定したメンバーの参照の型を表す"ICorDebugFunction"と"ICorDebugType"のインスタンスへのポインターのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="841a3-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841a3-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="841a3-107">See Also</span></span>  
    
 
