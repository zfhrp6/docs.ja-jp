---
title: ICorDebugAppDomain::Attach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a290ca162e5ab71b4184d166bcd00f1d0217cb94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="21171-102">ICorDebugAppDomain::Attach メソッド</span><span class="sxs-lookup"><span data-stu-id="21171-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="21171-103">アプリケーション ドメインに、デバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="21171-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21171-104">構文</span><span class="sxs-lookup"><span data-stu-id="21171-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="21171-105">コメント</span><span class="sxs-lookup"><span data-stu-id="21171-105">Remarks</span></span>  
 <span data-ttu-id="21171-106">アプリケーション ドメイン イベントを受信して、アプリケーション ドメインのデバッグを有効にするには、デバッガーをアタッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="21171-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21171-107">要件</span><span class="sxs-lookup"><span data-stu-id="21171-107">Requirements</span></span>  
 <span data-ttu-id="21171-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="21171-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21171-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21171-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21171-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21171-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21171-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21171-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
