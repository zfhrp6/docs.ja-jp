---
title: ICorDebugExceptionDebugEvent::GetFlags メソッド
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b9c07b010447b4a437febb4b60565111a85c8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415458"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="8ca10-102">ICorDebugExceptionDebugEvent::GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="8ca10-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="8ca10-103">例外をインターセプトできるかどうかを示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="8ca10-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca10-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ca10-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ca10-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ca10-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="8ca10-106">[out]ポインター、 [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)例外をインターセプトできるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="8ca10-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca10-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8ca10-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ca10-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ca10-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca10-109">要件</span><span class="sxs-lookup"><span data-stu-id="8ca10-109">Requirements</span></span>  
 <span data-ttu-id="8ca10-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ca10-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca10-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ca10-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ca10-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ca10-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ca10-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca10-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca10-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ca10-114">See Also</span></span>  
 [<span data-ttu-id="8ca10-115">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ca10-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="8ca10-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ca10-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
