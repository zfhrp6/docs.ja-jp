---
title: ICorDebugDebugEvent::GetEventKind メソッド
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bbc9581db839d9c0a48362eac2108f43665b0fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414857"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="fc104-102">ICorDebugDebugEvent::GetEventKind メソッド</span><span class="sxs-lookup"><span data-stu-id="fc104-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="fc104-103">この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="fc104-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc104-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc104-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc104-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc104-105">Parameters</span></span>  
 <span data-ttu-id="fc104-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="fc104-106">pDebugEventKind</span></span>  
 <span data-ttu-id="fc104-107">ポインター、 [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)イベントの種類を示す列挙メンバー。</span><span class="sxs-lookup"><span data-stu-id="fc104-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc104-108">コメント</span><span class="sxs-lookup"><span data-stu-id="fc104-108">Remarks</span></span>  
 <span data-ttu-id="fc104-109">`pDebugEventKind` の値に基づいて、`QueryInterface` を呼び出して、追加データを含むより正確なデバッグ イベント インターフェイスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="fc104-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc104-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc104-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc104-111">要件</span><span class="sxs-lookup"><span data-stu-id="fc104-111">Requirements</span></span>  
 <span data-ttu-id="fc104-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc104-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc104-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc104-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc104-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc104-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc104-115">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc104-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc104-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc104-116">See Also</span></span>  
 [<span data-ttu-id="fc104-117">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc104-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="fc104-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc104-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
