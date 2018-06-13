---
title: ICorDebugStackWalk::SetContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6025a31f26c635ac40dcc2e35e7017be1c81feba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423015"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext メソッド
セット、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)オブジェクトの現在のコンテキストのスレッドの有効なコンテキストにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `flag`  
 [in]A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)コンテキストは、スタック上のアクティブなフレームからまたはスタックのアンワインドによりコンテキストを取得するかどうかを示すフラグです。  
  
 `contextSize`  
 [in]割り当てサイズ、`CONTEXT`バッファー。  
  
 `context`  
 [in]`CONTEXT`バッファー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk`オブジェクトのコンテキストが正常に設定します。|  
|E_FAIL|`ICorDebugStackWalk`オブジェクトのコンテキストが設定されませんでした。|  
|E_INVALIDARG|コンテキストが null です。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|コンテキスト バッファーが小さすぎます。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 このメソッドは、スレッドの現在のコンテキストを変更しません。  
  
 無効なコンテキストを現在のコンテキストに設定すると、スタック ウォーカーにより予期しない結果があります可能性。  
  
 このコンテキストの正確なビットごとのコピーを取得するには、すぐに呼び出して、 [icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
