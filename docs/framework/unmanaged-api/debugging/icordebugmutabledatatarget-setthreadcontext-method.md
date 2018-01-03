---
title: "ICorDebugMutableDataTarget::SetThreadContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 077dfacc62c5bb450bc656c8fc102245d581eccc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext メソッド
スレッドのコンテキスト (レジスタの値) を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwThreadID`  
 [in] オペレーティング システム定義のスレッド識別子。  
  
 `contextSize`  
 [in]書き込まれる `pContext` バッファーのサイズ。  
  
 `pContext`  
 [in]書き込まれるバイト数へのポインター。  
  
## <a name="remarks"></a>コメント  
 `SetThreadContext` メソッドは、オペレーティング システム定義の `dwThreadID` 引数で指定されるスレッドの現在のコンテキストを更新します。 コンテキスト レコードの形式はにより示されるプラットフォームによって決まります、 [icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)メソッドです。 Windows では、これは、[コンテキスト](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx)構造体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugMutableDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
