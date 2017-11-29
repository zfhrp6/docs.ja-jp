---
title: "ICorProfilerCallback::UnmanagedToManagedTransition メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.UnmanagedToManagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45a2ceb53263e317c5c72695d6bc1e93f8f70bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition メソッド
アンマネージ コードからマネージ コードへの移行が発生したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]呼び出される関数の ID。  
  
 `reason`  
 [in]値、 [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) 、アンマネージ コードからマネージ コードに呼び出しのため、またはマネージのいずれかでと呼ばれるアンマネージ関数の戻り値のために、移行が発生したかどうかを示す列挙です。  
  
## <a name="remarks"></a>コメント  
 場合の値`reason`は COR_PRF_TRANSITION_RETURN と`functionId`が null でない ID が、アンマネージ関数とは決してがコンパイルされました - イン タイム (JIT) コンパイラを使用して関数。 アンマネージ関数では、名前とメタデータの一部など、それらに関連付けられている基本的な情報があります。  
  
 場合の値`reason`COR_PRF_TRANSITION_CALL には、呼び出された関数 (つまり、マネージ関数) されていない JIT でコンパイルされた可能性があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ManagedToUnmanagedTransition メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)  
 [C++ での明示的な PInvoke (DllImport 属性) の使用方法](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)  
 [C++ Interop (暗黙の PInvoke) の使用](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
