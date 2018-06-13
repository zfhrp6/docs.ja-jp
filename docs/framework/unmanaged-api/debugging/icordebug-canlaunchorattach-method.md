---
title: ICorDebug::CanLaunchOrAttach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f86cc83936dd8150ca6b3f28c9b6a624278e2b36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406292"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach メソッド
現在コンピューターとランタイムの構成のコンテキスト内で、新しいプロセスの起動または指定した既存のプロセスへのアタッチを実行するかどうかを示す HRESULT を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwProcessId`  
 [in]既存のプロセスの ID。  
  
 `win32DebuggingEnabled`  
 [in]渡す`true`Win32 デバッグを有効にするを起動しようとしています。 または、Win32 デバッグを有効になっている、それ以外を使用して接続を渡す場合`false`です。  
  
## <a name="return-value"></a>戻り値  
 デバッグ サービスを決定する、新しいプロセスの起動または特定のプロセスにアタッチする場合は S_OK は、現在のコンピューターとランタイムの構成に関する情報を指定できます。 HRESULT 値をとります。  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>コメント  
 このメソッドは、純粋な情報です。 インターフェイスはありません停止するを起動するかによって返される値に関係なく、プロセスへのアタッチ`CanLaunchOrAttach`です。  
  
 Win32 デバッグを有効に起動または attach Win32 デバッグを有効になっていると、パスにする場合`true`の`win32DebuggingEnabled`します。 によって返される HRESULT`CanLaunchOrAttach`は、このオプションを使用する場合に異なる場合があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
