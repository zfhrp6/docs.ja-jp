---
title: ICorDebugRegisterSet インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4b28d60b3a1da32d2d9db84aa92ca4c9bf769aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423196"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet インターフェイス
コードが現在実行されているコンピューター上で使用できるレジスタ セットを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetRegisters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|(現在のコードを実行しているコンピューター) 上の各レジスタの値を取得ビット マスクで指定されています。|  
|[GetRegistersAvailable メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|これで登録することを示す取得がビット マスク`ICorDebugRegisterSet`現在利用可能な。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|現在のスレッドのコンテキストを取得します。|  
|[SetRegisters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|.NET Framework version 2.0 の実装されていません。|  
|[SetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|.NET Framework 2.0 の実装されていません。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugRegisterSet`インターフェイスは、32 ビットのみレジスタをサポートしています。 使用して、 [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) IA 64 など、追加のレジスタが必要なプラットフォーム上のインターフェイスです。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
