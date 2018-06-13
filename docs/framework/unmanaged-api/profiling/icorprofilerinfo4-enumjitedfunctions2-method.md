---
title: ICorProfilerInfo4::EnumJITedFunctions2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b11c70fa7d423575b2dd1d2cc676908885a0fd4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457365"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2 メソッド
以前に JIT コンパイルされ、JIT 再コンパイルしていたすべての関数の列挙子を返します。 このメソッドは、置換、 [icorprofilerinfo 3::enumjitedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)メソッドの JIT 再コンパイルの Id を列挙できません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]ポインター、 [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)列挙子。  
  
## <a name="remarks"></a>コメント  
 このメソッドと重なる可能性があります`JITCompilation`など、コールバック、 [icorprofilercallback::jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)メソッドです。 返される列挙体には値が含まれています、`COR_PRF_FUNCTION::reJitId`フィールドです。 [Icorprofilerinfo 3::enumjitedfunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)ためこのメソッドに代わる、メソッドが JIT 再コンパイルの Id を列挙できません、`COR_PRF_FUNCTION::reJitId`フィールドは常に 0 に設定します。 `ICorProfilerInfo4::EnumJITedFunctions`のためにメソッドが JIT 再コンパイルの Id を列挙は、`COR_PRF_FUNCTION::reJitId`フィールドが適切に設定します。 なお、 [icorprofilerinfo 4::enumjitedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)一方、メソッドは、ガベージ コレクションをトリガーできます[icorprofilerinfo 3::enumjitedfunctions メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)は表示されません。  詳細については、次を参照してください。 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [EnumJITedFunctions メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)  
 [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
