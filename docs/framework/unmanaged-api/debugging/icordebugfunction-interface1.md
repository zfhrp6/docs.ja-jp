---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction
helpviewer_keywords: ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327ef9f74e94e3b1b20e78eb6a833038b5bfe16d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction-interface1"></a>ICorDebugFunction Interface1
マネージ関数またはマネージ メソッドを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|この関数の先頭にブレークポイントを作成します。|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|この関数のメンバーであるクラスを表す ICorDebugClass オブジェクトを取得します。|  
|[GetCurrentVersionNumber メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|この関数に対する最後の編集のバージョン番号を取得します。|  
|[GetILCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|この関数の Microsoft intermediate language (MSIL) コードを取得します。|  
|[GetLocalVarSigToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|これで表される関数の場合は、ローカル変数シグネチャのメタデータ トークンを取得`ICorDebugFunction`インスタンス。|  
|[GetModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|この関数が定義されているモジュールを取得します。|  
|[GetNativeCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|この関数のネイティブ コードを取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|この関数のメタデータ トークンを取得します。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugFunction`インターフェイスはジェネリック型パラメーターを持つ関数を表していません。 たとえば、`ICorDebugFunction`インスタンスを表します`Func<T>`ではなく`Func<string>`です。 呼び出す[icordebugilframe 2::enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)ジェネリック型パラメーターを取得します。  
  
 メソッドのメタデータ トークン、間のリレーションシップ`mdMethodDef`、およびメソッドの`ICorDebugFunction`オブジェクトは、関数にエディット コンティニュを許可するかどうかによって異なります。  
  
-   間に一対一のリレーションシップが存在する、関数、エディット コンティニュは許可されていない場合、`ICorDebugFunction`オブジェクトおよび`mdMethodDef`トークンです。 関数は、1 つ`ICorDebugFunction`オブジェクトと 1 つ`mdMethodDef`トークンです。  
  
-   間多対一リレーションシップが存在する場合は、関数では、エディット コンティニュは使用して、`ICorDebugFunction`オブジェクトおよび`mdMethodDef`トークンです。 つまり、関数が多数のインスタンスを必要があります`ICorDebugFunction`、関数のバージョンごとに 1 つが 1 人だけ`mdMethodDef`トークンです。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
