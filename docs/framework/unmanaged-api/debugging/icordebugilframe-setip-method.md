---
title: ICorDebugILFrame::SetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed7de70c8ea26f46f44abb3e063c6e4c4b115666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414491"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP メソッド
Microsoft intermediate language (MSIL) コード内の指定したオフセット位置に、命令ポインターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `nOffset`  
 MSIL コード内のオフセットの位置。  
  
## <a name="remarks"></a>コメント  
 呼び出す`SetIP`すぐにすべてのフレームと現在のスレッドのチェーンが無効にします。 デバッガーには、呼び出しの後にフレーム情報が必要がある場合`SetIP`、新しいスタック トレースを実行する必要があります。  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)に有効な状態でスタック フレームを維持しようとします。 ただし、場合でも、有効な状態では、フレームは、まだある可能性があります初期化されていないローカル変数などの問題です。 呼び出し元は、実行中のプログラムの一貫性を保証します。  
  
 64 ビット プラットフォームでは、上の命令ポインターを移動できません、`catch`または`finally`ブロックします。 場合`SetIP`が呼び出された 64 ビット プラットフォームで、このような移動をするためには、エラーを示す HRESULT を返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
