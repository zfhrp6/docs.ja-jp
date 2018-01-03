---
title: "ICorDebugStepper::SetRangeIL メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetRangeIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 658f0164a73cfb5dbab0379eda2f61505865d2c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL メソッド
指定する値を設定するかどうかを呼び出す[icordebugstepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)または Microsoft の基準としたネイティブ コードへの相対値の中間 language (MSIL) コードがステップ インされているメソッドの引数を渡すを通じてします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bIL`  
 [in]設定`true`な MSIL コード相対の範囲を指定します。 設定`false`範囲がネイティブ コードの基準としたことを指定します。 既定値は `true` です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
