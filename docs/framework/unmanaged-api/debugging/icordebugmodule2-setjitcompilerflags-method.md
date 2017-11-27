---
title: "ICorDebugModule2::SetJITCompilerFlags メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42eea356214fedb22a2f60842f6007f3eb6a0e2a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="a764a-102">ICorDebugModule2::SetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="a764a-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="a764a-103">この ICorDebugModule2 の・ イン タイム (JIT) コンパイルを制御するフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="a764a-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a764a-104">構文</span><span class="sxs-lookup"><span data-stu-id="a764a-104">Syntax</span></span>  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a764a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a764a-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="a764a-106">[in]ビットごとの組み合わせ、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列挙値。</span><span class="sxs-lookup"><span data-stu-id="a764a-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a764a-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a764a-107">Remarks</span></span>  
 <span data-ttu-id="a764a-108">場合、`dwFlags`値が有効で、`SetJITCompilerFlags`メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="a764a-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="a764a-109">`SetJITCompilerFlags`メソッド内からのみ呼び出すことができます、 [icordebugmanagedcallback::loadmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)このモジュールのコールバック。</span><span class="sxs-lookup"><span data-stu-id="a764a-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="a764a-110">後の呼び出しを行う、`ICorDebugManagedCallback::LoadModule`コールバックにが配信されて失敗します。</span><span class="sxs-lookup"><span data-stu-id="a764a-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="a764a-111">エディット コンティニュは 64 ビット プラットフォームまたは Win9x プラットフォームでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a764a-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="a764a-112">そのため、呼び出す場合、`SetJITCompilerFlags`これら 2 つのプラットフォームで設定 CORDEBUG_JIT_ENABLE_ENC フラグのいずれかのメソッド`dwFlags`、`SetJITCompilerFlags`エディット コンティニュなどには、メソッドおよびすべてのメソッドを特定[ICorDebugModule2:。ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)は失敗します。</span><span class="sxs-lookup"><span data-stu-id="a764a-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a764a-113">要件</span><span class="sxs-lookup"><span data-stu-id="a764a-113">Requirements</span></span>  
 <span data-ttu-id="a764a-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a764a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a764a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a764a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a764a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a764a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a764a-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a764a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
