---
title: "ICorProfilerCallback::ManagedToUnmanagedTransition メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ManagedToUnmanagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9da8dd44d5b87cd1c65b8b8837c9dd378039d332
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition メソッド
マネージ コードからアンマネージ コードへの移行が発生したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]呼び出される関数の ID。  
  
 `reason`  
 [in]値、 [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)をマネージ コードからアンマネージ コードに呼び出しのため、またはアンマネージによって呼び出されるマネージ関数の戻り値のために、移行が発生したかどうかを示す列挙体です。  
  
## <a name="remarks"></a>コメント  
 場合の値`reason`COR_PRF_TRANSITION_CALL、ID こと、アンマネージ関数は決してコンパイルされたジャスト イン タイムのコンパイラを使用してこの関数は、します。 アンマネージ関数には、名前とメタデータの一部など、それらに関連付けられている基本的な情報が含まれています。 暗黙のプラットフォームを使用して、アンマネージ関数が呼び出された場合は、呼び出し (PInvoke)、ランタイムは、呼び出し先との値を特定できません`functionId`は null になります。 暗黙の PInvoke の詳細については、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [UnmanagedToManagedTransition メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [C++ での明示的な PInvoke (DllImport 属性) の使用方法](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
