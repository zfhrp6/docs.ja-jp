---
title: "CorDebugCodeInvokePurpose 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugInvokePurpose
api_location: mscordbi.dll
api_type: COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e87e5d8baf3ff7c87efe8f6bd96f8fd806527363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="f3abb-102">CorDebugCodeInvokePurpose 列挙体</span><span class="sxs-lookup"><span data-stu-id="f3abb-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="f3abb-103">エクスポートされた関数がマネージ コードを呼び出す理由を示します。</span><span class="sxs-lookup"><span data-stu-id="f3abb-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3abb-104">構文</span><span class="sxs-lookup"><span data-stu-id="f3abb-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="f3abb-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f3abb-105">Members</span></span>  
  
|<span data-ttu-id="f3abb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f3abb-106">Member</span></span>|<span data-ttu-id="f3abb-107">説明</span><span class="sxs-lookup"><span data-stu-id="f3abb-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="f3abb-108">None または不明です。</span><span class="sxs-lookup"><span data-stu-id="f3abb-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="f3abb-109">マネージ コードは、逆 p-invoke などのすべてのマネージ エントリ ポイントを実行します。</span><span class="sxs-lookup"><span data-stu-id="f3abb-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="f3abb-110">より詳細な目的は、ランタイムによって認識されません。</span><span class="sxs-lookup"><span data-stu-id="f3abb-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="f3abb-111">マネージ コードは、静的コンストラクターを実行します。</span><span class="sxs-lookup"><span data-stu-id="f3abb-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="f3abb-112">マネージ コードは、呼び出されたいくつかのインターフェイス メソッドの実装を実行します。</span><span class="sxs-lookup"><span data-stu-id="f3abb-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3abb-113">コメント</span><span class="sxs-lookup"><span data-stu-id="f3abb-113">Remarks</span></span>  
 <span data-ttu-id="f3abb-114">この列挙体を使って、 [icordebugprocess 6::getexportstepinfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)マネージ コードをステップ実行に関する情報を提供するメソッド。</span><span class="sxs-lookup"><span data-stu-id="f3abb-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3abb-115">この列挙体は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="f3abb-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3abb-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="f3abb-116">Requirements</span></span>  
 <span data-ttu-id="f3abb-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3abb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3abb-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3abb-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3abb-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3abb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3abb-120">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3abb-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3abb-121">参照</span><span class="sxs-lookup"><span data-stu-id="f3abb-121">See Also</span></span>  
 [<span data-ttu-id="f3abb-122">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f3abb-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="f3abb-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f3abb-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
