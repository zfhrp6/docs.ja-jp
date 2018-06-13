---
title: ICorDebugType Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de2871b406bb9da84d20d7c526ad4a703baae409
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422872"
---
# <a name="icordebugtype-interface1"></a>ICorDebugType Interface1
型、基本または複雑な (つまり、ユーザー定義) を表します。 型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateTypeParameters メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|ジェネリックを参照する ICorDebugTypeEnum へのインターフェイス ポインターを取得<xref:System.Type>これによって参照されるクラスのパラメーター`ICorDebugType`です。|  
|[GetBase メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|インターフェイス ポインターを取得、`ICorDebugType`これによって参照されるクラスの基底クラスを参照する`ICorDebugType`が存在する場合は、します。|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|この型指定されたコンス トラクターを参照する ICorDebugClass へのインターフェイス ポインターを取得`ICorDebugType`です。|  
|[GetFirstTypeParameter メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|インターフェイス ポインターを取得、`ICorDebugType`を参照する最初のジェネリック<xref:System.Type>これによって参照されるクラスのコンス トラクターのパラメーター`ICorDebugType`です。|  
|[GetRank メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|配列型の次元数を取得します。|  
|[GetStaticFieldValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|トークンを指定したスタック フレームに指定したフィールドによって参照される静的フィールドの値を含む ICorDebugValue にインターフェイス ポインターを取得します。|  
|[GetType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|共通言語ランタイムのネイティブ型を記述する CorElementType 値を取得<xref:System.Type>これによって参照される`ICorDebugType`です。|  
  
## <a name="remarks"></a>コメント  
 場合は、型がジェネリック、`ICorDebugClass`インスタンス化されていない型を表します。 `ICorDebugType`インターフェイスはジェネリック型のインスタンスを表します。 ハッシュ テーブルなど、\<K, V > で表されます`ICorDebugClass`であるのに対し Hashtable\<Int32, String > で表されます`ICorDebugType`です。  
  
 非ジェネリック型は型が両方によって表される`ICorDebugClass`と`ICorDebugType`です。 後者のインターフェイスは、型のインスタンス化に対処するには、.NET Framework version 2.0 で導入されました。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
