---
title: ICorDebugAppDomain Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84a11b6264ac0e241c1975eea5626edbdddce206
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406878"
---
# <a name="icordebugappdomain-interface1"></a>ICorDebugAppDomain Interface1
アプリケーション ドメインをデバッグするためのメソッドを提供します。 このインターフェイスは、ICorDebugController のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Attach メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|アプリケーション ドメインに、デバッガーをアタッチします。|  
|[EnumerateAssemblies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|アプリケーション ドメイン内のアセンブリの列挙子を取得します。|  
|[EnumerateBreakpoints メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|アプリケーション ドメインですべてのアクティブなブレークポイントの列挙子を取得します。|  
|[EnumerateSteppers メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|アプリケーション ドメイン内のすべてのアクティブ ステッパの列挙子を取得します。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|アプリケーション ドメインの一意の ID を取得します。|  
|[GetModuleFromMetaDataInterface メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|指定されたメタデータ インターフェイス ICorDebugModule オブジェクトを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|アプリケーション ドメインの名前を取得します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|共通言語ランタイム (CLR) のアプリケーション ドメインへのインターフェイス ポインターを取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|アプリケーション ドメインを含むプロセスを取得します。|  
|[IsAttached メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|アプリケーション ドメインに、デバッガーがアタッチされているかどうかを判断します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
