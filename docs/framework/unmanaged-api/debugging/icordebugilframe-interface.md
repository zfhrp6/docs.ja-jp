---
title: ICorDebugILFrame Interface1
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
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1db53f50e942e70517fc06dfd90e75d04158ea9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe-interface1"></a>ICorDebugILFrame Interface1
Microsoft intermediate language (MSIL) コードのスタック フレームを表します。 このインターフェイスは、ICorDebugFrame インターフェイスのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanSetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|命令ポインターを指定したオフセット位置に設定しても安全であるかどうかを示す値を取得します。|  
|[EnumerateArguments メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|引数のこのフレームの列挙子を取得します。|  
|[EnumerateLocalVariables メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|このフレームのローカル変数の列挙子を取得します。|  
|[GetArgument メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|MSIL のこのスタック フレーム内には、指定された引数の値を取得します。|  
|[GetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|命令ポインターの値および命令ポインターの値の取得方法を説明するビットごとの組み合わせの値を取得します。|  
|[GetLocalVariable メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|MSIL のこのスタック フレーム内には、指定されたローカル変数の値を取得します。|  
|[GetStackDepth メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|実装されていません。|  
|[GetStackValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|実装されていません。|  
|[SetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|命令ポインターを MSIL コードで指定されたオフセット位置に設定します。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugILFrame`インターフェイスは、特殊な ICorDebugFrame インターフェイスです。 使用されているフレームをコンパイルされた MSIL コード フレームまたは・ イン タイム (JIT) のいずれか。 JIT コンパイルのフレームでは、両方を実装、`ICorDebugILFrame`インターフェイスと ICorDebugNativeFrame インターフェイスです。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
