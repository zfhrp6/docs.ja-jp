---
title: "ICorDebugManagedCallback::UpdateModuleSymbols メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UpdateModuleSymbols
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad5a84268f3810a1fb73a21a6bd8106e82ccbd78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols メソッド
共通言語ランタイム モジュールのシンボルが変更されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]ICorDebugAppDomain を表すオブジェクトを含むモジュールのシンボルが変更されたが、アプリケーション ドメインへのポインター。  
  
 `pModule`  
 [in]シンボルが変更されたが、モジュールを表す ICorDebugModule オブジェクトへのポインター。  
  
 `pSymbolStream`  
 [in]Win32 COM へのポインター`IStream`変更済みのシンボルを格納するオブジェクト。  
  
## <a name="remarks"></a>コメント  
 このメソッドを呼び出すことによってモジュールのシンボルのデバッガーのビューを更新する機会を提供する[isymunmanagedreader::updatesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)または[isymunmanagedreader::replacesymbolstore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)です。  
  
 このコールバックに、同じモジュールの複数回発生します。  
  
 デバッガーは、バインドされていないソース レベルのブレークポイントをバインドする試してください。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
