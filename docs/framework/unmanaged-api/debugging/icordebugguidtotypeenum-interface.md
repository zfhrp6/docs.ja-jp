---
title: ICorDebugGuidToTypeEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91d653587d5b7c35a2a43c7eed7c4bf33e5401f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416752"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum インターフェイス
Guid のセットおよび ICorDebugType インスタンスによって表されますが、対応する型の間のマッピングを定義する列挙子を提供します。 このインターフェイスは、ICorDebugEnum インターフェイスからメソッドを継承します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Icordebugguidtotypeenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|指定した数を取得[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)情報を入力する Guid をマップするインスタンス。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugGuidToTypeEnum`インターフェイス オブジェクトを呼び出すことによって取得できる、 [icordebugappdomain 3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)メソッドです。 デバッガーは、このインターフェイスを呼び出すことができます[次](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)を取得する方法[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)のマッピングを表すオブジェクトの表現を管理する[!INCLUDE[wrt](../../../../includes/wrt-md.md)]に読み込まれた型、呼び出しに使用するアプリケーション ドメイン、 [icordebugappdomain 3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
