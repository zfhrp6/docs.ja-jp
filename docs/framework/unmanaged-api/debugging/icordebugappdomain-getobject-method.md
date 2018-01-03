---
title: "ICorDebugAppDomain::GetObject メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetObject
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f8206c6e5efbee8522f425f9078d99a39bbdd42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="9280b-102">ICorDebugAppDomain::GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="9280b-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="9280b-103">共通言語ランタイム (CLR) のアプリケーション ドメインへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9280b-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9280b-104">構文</span><span class="sxs-lookup"><span data-stu-id="9280b-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9280b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9280b-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="9280b-106">[out]CLR のアプリケーション ドメインを表す ICorDebugValue インターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9280b-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9280b-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9280b-107">Return Value</span></span>  
 <span data-ttu-id="9280b-108">マネージ場合<xref:System.AppDomain?displayProperty=nameWithType>オブジェクトは、このアプリケーション ドメインの構築されていない、メソッドが返されます`S_FALSE`配置`NULL`で`*ppObject`です。</span><span class="sxs-lookup"><span data-stu-id="9280b-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9280b-109">コメント</span><span class="sxs-lookup"><span data-stu-id="9280b-109">Remarks</span></span>  
 <span data-ttu-id="9280b-110">プロセス内の各アプリケーション ドメインは、管理されている必要があります<xref:System.AppDomain?displayProperty=nameWithType>を表すそのランタイム内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9280b-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="9280b-111">この関数は、管理に対応する ICorDebugValue インターフェイス オブジェクトを取得します。<xref:System.AppDomain?displayProperty=nameWithType>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9280b-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9280b-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="9280b-112">Requirements</span></span>  
 <span data-ttu-id="9280b-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9280b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9280b-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9280b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9280b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9280b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9280b-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9280b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
