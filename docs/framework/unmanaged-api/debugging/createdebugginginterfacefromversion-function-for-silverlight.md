---
title: "CreateDebuggingInterfaceFromVersion 関数 (Silverlight 用)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c38171c5887bb207b3692e9fa92aa2be2bc72a27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="69257-102">CreateDebuggingInterfaceFromVersion 関数 (Silverlight 用)</span><span class="sxs-lookup"><span data-stu-id="69257-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="69257-103">返される共通言語ランタイム (CLR) バージョン文字列を受け入れる、 [CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)、し、対応するデバッガー インターフェイスを返します (通常、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md))。</span><span class="sxs-lookup"><span data-stu-id="69257-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69257-104">構文</span><span class="sxs-lookup"><span data-stu-id="69257-104">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69257-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69257-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="69257-106">[in]によって返されるデバッグ対象により、CLR のバージョン文字列、 [CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="69257-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="69257-107">[out] COM オブジェクト (`IUnknown`) へのポインターのポインター。</span><span class="sxs-lookup"><span data-stu-id="69257-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="69257-108">このオブジェクトにキャストされます、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)オブジェクトに返されます。</span><span class="sxs-lookup"><span data-stu-id="69257-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69257-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="69257-109">Return Value</span></span>  
 <span data-ttu-id="69257-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="69257-110">S_OK</span></span>  
 <span data-ttu-id="69257-111">`ppCordb`実装する有効なオブジェクトを参照して、 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="69257-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="69257-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="69257-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="69257-113">`szDebuggeeVersion` または `ppCordb` が null です。</span><span class="sxs-lookup"><span data-stu-id="69257-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="69257-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="69257-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="69257-115">CLR デバッグに必要なコンポーネントが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="69257-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="69257-116">つまり、mscordbi.dll または mscordaccore.dll が対象の CoreCLR.dll と同じディレクトリに見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="69257-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="69257-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="69257-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="69257-118">mscordbi.dll または mscordaccore.dll が対象の CoreCLR.dll と同じバージョンではありません。</span><span class="sxs-lookup"><span data-stu-id="69257-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="69257-119">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="69257-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="69257-120">返すことができません、 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="69257-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69257-121">コメント</span><span class="sxs-lookup"><span data-stu-id="69257-121">Remarks</span></span>  
 <span data-ttu-id="69257-122">返されるインターフェイスは、対象のプロセス内の CLR にアタッチして CLR が実行しているマネージ コードをデバッグする機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="69257-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69257-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="69257-123">Requirements</span></span>  
 <span data-ttu-id="69257-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="69257-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69257-125">**ヘッダー:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="69257-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="69257-126">**ライブラリ:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="69257-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="69257-127">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="69257-127">**.NET Framework Versions:** 3.5 SP1</span></span>
