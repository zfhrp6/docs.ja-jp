---
title: ICorDebugAssembly::GetAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e22d112d1414b13033f73723821e5e4b5764e1c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401980"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="7d3e4-102">ICorDebugAssembly::GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="7d3e4-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="7d3e4-103">インターフェイス ポインターを格納しているアプリケーション ドメインに取得`ICorDebugAssembly`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="7d3e4-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d3e4-104">構文</span><span class="sxs-lookup"><span data-stu-id="7d3e4-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d3e4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d3e4-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="7d3e4-106">[out]アプリケーション ドメインを表す ICorDebugAppDomain インターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7d3e4-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d3e4-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7d3e4-107">Remarks</span></span>  
 <span data-ttu-id="7d3e4-108">このアセンブリがシステム アセンブリ場合`GetAppDomain`は null を返します。</span><span class="sxs-lookup"><span data-stu-id="7d3e4-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d3e4-109">要件</span><span class="sxs-lookup"><span data-stu-id="7d3e4-109">Requirements</span></span>  
 <span data-ttu-id="7d3e4-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d3e4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d3e4-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d3e4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d3e4-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d3e4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d3e4-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d3e4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
