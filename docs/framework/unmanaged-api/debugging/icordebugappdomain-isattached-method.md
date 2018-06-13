---
title: ICorDebugAppDomain::IsAttached メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0412089fee27e556c2f9230e9b34de3391b9bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402562"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="488ed-102">ICorDebugAppDomain::IsAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="488ed-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="488ed-103">アプリケーション ドメインに、デバッガーがアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="488ed-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488ed-104">構文</span><span class="sxs-lookup"><span data-stu-id="488ed-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="488ed-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="488ed-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="488ed-106">[out]`true`デバッガーがアプリケーション ドメインに接続されている、それ以外の場合は`false`します。</span><span class="sxs-lookup"><span data-stu-id="488ed-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="488ed-107">コメント</span><span class="sxs-lookup"><span data-stu-id="488ed-107">Remarks</span></span>  
 <span data-ttu-id="488ed-108">ICorDebugController メソッドは、デバッガーは、アプリケーション ドメインにアタッチされるまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="488ed-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="488ed-109">要件</span><span class="sxs-lookup"><span data-stu-id="488ed-109">Requirements</span></span>  
 <span data-ttu-id="488ed-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="488ed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="488ed-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="488ed-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="488ed-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="488ed-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="488ed-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="488ed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
