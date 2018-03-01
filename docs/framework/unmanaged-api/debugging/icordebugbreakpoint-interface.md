---
title: ICorDebugBreakpoint Interface1
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
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd2c4245b5e3dcc4f7b989a3ca9add8d568467cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpoint-interface1"></a>ICorDebugBreakpoint Interface1
関数、または値のウォッチ ポイントでのブレークポイントを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Activate メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|これのアクティブな状態を設定`ICorDebugBreakpoint`です。|  
|[IsActive メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|示す値を取得するかどうかこの`ICorDebugBreakpoint`がアクティブです。|  
  
## <a name="remarks"></a>コメント  
 ブレークポイントでは、条件式は直接サポートしていません。 デバッガーがの上にそれを実装する必要がありますこのような機能を使用する場合は、`ICorDebugBreakpoint`です。  
  
 ICorDebugFunctionBreakpoint インターフェイスを拡張`ICorDebugBreakpoint`関数内のブレークポイントをサポートするためにします。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
