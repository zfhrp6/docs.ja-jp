---
title: ICorDebugModuleDebugEvent::GetModule メソッド
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56ce5b3f5fb3c6d2a00c407afc303895273c2251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419492"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="3fe42-102">ICorDebugModuleDebugEvent::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="3fe42-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="3fe42-103">ロードまたはアンロードされたばかりのマージ モジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3fe42-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe42-104">構文</span><span class="sxs-lookup"><span data-stu-id="3fe42-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fe42-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3fe42-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="3fe42-106">[out]マージされたモジュールがロードまたはアンロードばかりを表す ICorDebugModule オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3fe42-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fe42-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3fe42-107">Remarks</span></span>  
 <span data-ttu-id="3fe42-108">呼び出すことができます、 [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)モジュールの読み込みまたはアンロードされたかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="3fe42-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fe42-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3fe42-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fe42-110">要件</span><span class="sxs-lookup"><span data-stu-id="3fe42-110">Requirements</span></span>  
 <span data-ttu-id="3fe42-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3fe42-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fe42-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fe42-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fe42-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fe42-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fe42-114">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fe42-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe42-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fe42-115">See Also</span></span>  
 [<span data-ttu-id="3fe42-116">ICorDebugModuleDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fe42-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [<span data-ttu-id="3fe42-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fe42-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
