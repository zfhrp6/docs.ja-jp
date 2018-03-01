---
title: "ICorDebugStepper::StepRange メソッド"
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
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a02efe1b701506cc3de695c5b79d5e9c84b25b8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange メソッド
Icordebugstepper をシングル ステップ実行し、指定された範囲の最後以外のコードに達したときに返されるその格納スレッドを表示します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bStepIn`  
 [in]設定`true`スレッド内で呼び出される関数にステップ インします。 設定`false`をステップ オーバー関数。  
  
 `ranges`  
 [in]COR_DEBUG_STEP_RANGE 構造体の配列、それぞれの範囲を指定します。  
  
 `cRangeCount`  
 [in] `ranges` 配列のサイズ。  
  
## <a name="remarks"></a>コメント  
 `StepRange`のような方法は、機能、 [icordebugstepper::step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)メソッド、特定の範囲外のコードまでに完了しないする点を除いてに達した。  
  
 これは、一度に 1 つの命令をステップ実行するよりも効率的で指定できます。 範囲は、ステッパのフレームの先頭からのオフセットのペアのリストとして指定します。  
  
 範囲は、メソッドの Microsoft intermediate language (MSIL) コードです。 呼び出す[icordebugstepper::setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)で`false`メソッドのネイティブ コードの基準とした範囲にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
