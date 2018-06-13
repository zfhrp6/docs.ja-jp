---
title: CorDebugCodeInvokeKind 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf777214c015f0bbc434e3123d3ec7ef7f723549
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405653"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="7d115-102">CorDebugCodeInvokeKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="7d115-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="7d115-103">エクスポートされた関数がマネージ コードを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7d115-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d115-104">構文</span><span class="sxs-lookup"><span data-stu-id="7d115-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="7d115-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="7d115-105">Members</span></span>  
  
|<span data-ttu-id="7d115-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7d115-106">Member</span></span>|<span data-ttu-id="7d115-107">説明</span><span class="sxs-lookup"><span data-stu-id="7d115-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="7d115-108">マネージ コードがこのメソッドによって呼び出される場合は、明示的なイベントまたはブレークポイントによって後で配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d115-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="7d115-109">または</span><span class="sxs-lookup"><span data-stu-id="7d115-109">--or--</span></span><br /><br /> <span data-ttu-id="7d115-110">このメソッドが呼び出すマネージ コードは、停止する簡単な方法がないため、一部を見逃す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d115-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="7d115-111">または</span><span class="sxs-lookup"><span data-stu-id="7d115-111">--or--</span></span><br /><br /> <span data-ttu-id="7d115-112">メソッドがマネージ コードを呼び出さない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d115-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="7d115-113">このメソッドは、戻り命令を使用してマネージ コードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7d115-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="7d115-114">ステップ アウトは次のマネージ コードに到達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d115-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="7d115-115">このメソッドは、末尾呼び出しを使用してマネージ コードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7d115-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="7d115-116">いずれかの呼び出し命令をシングル ステップ実行およびステップ オーバーすると、マネージ コードに到達します。</span><span class="sxs-lookup"><span data-stu-id="7d115-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d115-117">コメント</span><span class="sxs-lookup"><span data-stu-id="7d115-117">Remarks</span></span>  
 <span data-ttu-id="7d115-118">この列挙体を使って、 [icordebugprocess 6::getexportstepinfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)マネージ コードをステップ実行に関する情報を提供するメソッド。</span><span class="sxs-lookup"><span data-stu-id="7d115-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d115-119">この列挙体は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="7d115-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d115-120">要件</span><span class="sxs-lookup"><span data-stu-id="7d115-120">Requirements</span></span>  
 <span data-ttu-id="7d115-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d115-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d115-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d115-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d115-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d115-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d115-124">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d115-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d115-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d115-125">See Also</span></span>  
 [<span data-ttu-id="7d115-126">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="7d115-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="7d115-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="7d115-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
