---
title: CorDebugInternalFrameType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b42a7fc54af56149b602b337e4a6c853c270cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406358"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType 列挙型
スタック フレームの型を示します。 この列挙体を使って、 [icordebuginternalframe::getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`STUBFRAME_NONE`|null 値。 `ICorDebugInternalFrame::GetFrameType`メソッドは決してこの値を返します。|  
|`STUBFRAME_M2U`|マネージ、アンマネージのスタブ フレームです。|  
|`STUBFRAME_U2M`|スタブのアンマネージからマネージ フレームでです。|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|アプリケーション ドメイン間で移行します。|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|軽量のメソッドの呼び出しです。|  
|`STUBFRAME_FUNC_EVAL`|関数の評価の開始。|  
|`STUBFRAME_INTERNALCALL`|共通言語ランタイムの内部呼び出しです。|  
|`STUBFRAME_CLASS_INIT`|クラスの初期化の開始。|  
|`STUBFRAME_EXCEPTION`|スローされる例外。|  
|`STUBFRAME_SECURITY`|コード アクセス セキュリティに使用するフレーム。|  
|`STUBFRAME_JIT_COMPILATION`|ランタイムは、メソッドの JIT コンパイルです。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
