---
title: "ICorDebugModule2::SetJITCompilerFlags メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfc25e9ce15996360cd0e3c68805d3707b325f79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags メソッド
この ICorDebugModule2 の・ イン タイム (JIT) コンパイルを制御するフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFlags`  
 [in]ビットごとの組み合わせ、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列挙値。  
  
## <a name="remarks"></a>コメント  
 場合、`dwFlags`値が有効で、`SetJITCompilerFlags`メソッドは失敗します。  
  
 `SetJITCompilerFlags`メソッド内からのみ呼び出すことができます、 [icordebugmanagedcallback::loadmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)このモジュールのコールバック。 後の呼び出しを行う、`ICorDebugManagedCallback::LoadModule`コールバックにが配信されて失敗します。  
  
 エディット コンティニュは 64 ビット プラットフォームまたは Win9x プラットフォームでサポートされていません。 そのため、呼び出す場合、`SetJITCompilerFlags`これら 2 つのプラットフォームで設定 CORDEBUG_JIT_ENABLE_ENC フラグのいずれかのメソッド`dwFlags`、`SetJITCompilerFlags`エディット コンティニュなどには、メソッドおよびすべてのメソッドを特定[ICorDebugModule2:。ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)は失敗します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
