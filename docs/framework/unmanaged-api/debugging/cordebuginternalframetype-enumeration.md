---
title: "CorDebugInternalFrameType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65e970563ec3958deddb0aa1d89e10b0da70f0a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="074ca-102">CorDebugInternalFrameType 列挙型</span><span class="sxs-lookup"><span data-stu-id="074ca-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="074ca-103">スタック フレームの型を示します。</span><span class="sxs-lookup"><span data-stu-id="074ca-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="074ca-104">この列挙体を使って、 [icordebuginternalframe::getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="074ca-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="074ca-105">構文</span><span class="sxs-lookup"><span data-stu-id="074ca-105">Syntax</span></span>  
  
```  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="074ca-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="074ca-106">Members</span></span>  
  
|<span data-ttu-id="074ca-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="074ca-107">Member</span></span>|<span data-ttu-id="074ca-108">説明</span><span class="sxs-lookup"><span data-stu-id="074ca-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="074ca-109">null 値。</span><span class="sxs-lookup"><span data-stu-id="074ca-109">A null value.</span></span> <span data-ttu-id="074ca-110">`ICorDebugInternalFrame::GetFrameType`メソッドは決してこの値を返します。</span><span class="sxs-lookup"><span data-stu-id="074ca-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="074ca-111">マネージ、アンマネージのスタブ フレームです。</span><span class="sxs-lookup"><span data-stu-id="074ca-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="074ca-112">スタブのアンマネージからマネージ フレームでです。</span><span class="sxs-lookup"><span data-stu-id="074ca-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="074ca-113">アプリケーション ドメイン間で移行します。</span><span class="sxs-lookup"><span data-stu-id="074ca-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="074ca-114">軽量のメソッドの呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="074ca-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="074ca-115">関数の評価の開始。</span><span class="sxs-lookup"><span data-stu-id="074ca-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="074ca-116">共通言語ランタイムの内部呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="074ca-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="074ca-117">クラスの初期化の開始。</span><span class="sxs-lookup"><span data-stu-id="074ca-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="074ca-118">スローされる例外。</span><span class="sxs-lookup"><span data-stu-id="074ca-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="074ca-119">コード アクセス セキュリティに使用するフレーム。</span><span class="sxs-lookup"><span data-stu-id="074ca-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="074ca-120">ランタイムは、メソッドの JIT コンパイルです。</span><span class="sxs-lookup"><span data-stu-id="074ca-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="074ca-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="074ca-121">Requirements</span></span>  
 <span data-ttu-id="074ca-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="074ca-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="074ca-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="074ca-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="074ca-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="074ca-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="074ca-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="074ca-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074ca-126">参照</span><span class="sxs-lookup"><span data-stu-id="074ca-126">See Also</span></span>  
 [<span data-ttu-id="074ca-127">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="074ca-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
