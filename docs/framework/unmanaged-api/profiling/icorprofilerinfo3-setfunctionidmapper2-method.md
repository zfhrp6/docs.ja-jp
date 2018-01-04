---
title: "ICorProfilerInfo3::SetFunctionIDMapper2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a58b01345fe1acb7434b8896ebbc8548ab68a98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a>ICorProfilerInfo3::SetFunctionIDMapper2 メソッド
`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。 このメソッドによって拡張、 [icorprofilerinfo::setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)プロファイラーはランタイムの間であいまいさを解消を使用して追加のデータのパラメーターを持つメソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFunc`  
 [in]ポインター、 [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)実装にマップすると呼び出される、`FunctionID`値を代替値にします。  
  
 `clientData`  
 [in]渡されるたびにポインター [FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)関数の現在のランタイムによって行われた呼び出しです。 プロファイラーは、この情報を使用して、ランタイムの間であいまいさを解消することができます。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>コメント  
 FunctionID 値の代替手段は、プロファイラーの関数の開始フックと終了フックに渡されます ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)、および[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md);または[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)、および[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) で指定されている、 [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)または[SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)メソッドです。  
  
 `FunctionIDMapper2`メソッドを 1 回だけ設定できます。 に設定することをお勧め、 [icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
