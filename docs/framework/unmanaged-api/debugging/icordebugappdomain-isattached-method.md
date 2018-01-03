---
title: "ICorDebugAppDomain::IsAttached メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1af550de7198041a885a788d6b36349c8e1c091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="a7ea2-102">ICorDebugAppDomain::IsAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="a7ea2-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="a7ea2-103">アプリケーション ドメインに、デバッガーがアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a7ea2-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ea2-104">構文</span><span class="sxs-lookup"><span data-stu-id="a7ea2-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7ea2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a7ea2-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="a7ea2-106">[out]`true`デバッガーがアプリケーション ドメインに接続されている、それ以外の場合は`false`します。</span><span class="sxs-lookup"><span data-stu-id="a7ea2-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ea2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a7ea2-107">Remarks</span></span>  
 <span data-ttu-id="a7ea2-108">ICorDebugController メソッドは、デバッガーは、アプリケーション ドメインにアタッチされるまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="a7ea2-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ea2-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="a7ea2-109">Requirements</span></span>  
 <span data-ttu-id="a7ea2-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7ea2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ea2-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7ea2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7ea2-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7ea2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7ea2-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ea2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
