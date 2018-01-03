---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList メソッド
モニター ロックに関連付けられているイベントでは、キュー内のスレッドの順序付きリストを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppThreadEnum`  
 [out]スレッドの順序付きリストを提供する ICorDebugThreadEnum 列挙子。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|The list is not empty.|  
|S_FALSE|リストが空です。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 一覧の最初のスレッドは、次の呼び出しによってリリースされた最初のスレッド<xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>です。 一覧で、[次へ] のスレッドは、次の呼び出し時に解放されます。  
  
 リストが空でない場合、このメソッドは、S_OK を返します。 メソッドは S_FALSE; を返します、リストが空の場合ここでは、列挙体がまだ有効では空です。  
  
 どちらの場合、列挙インターフェイスは、現在の同期状態の期間に対してのみ使用可能です。 ただし、これから管理されているスレッドのインターフェイスは、スレッドを終了するまで無効です。  
  
 場合`ppThreadEnum`は有効なポインターではありません、結果は未定義です。  
  
 スレッドが、モニターを待機している場合、これを確認できないように、エラーが発生した場合、メソッドは失敗を示す HRESULT を返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
