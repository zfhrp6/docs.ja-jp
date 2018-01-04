---
title: "ICorProfilerInfo3::EnumJITedFunctions メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.EnumJITedFunctions Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11a6b34be4f9bf046749941ac12895bf7040e331
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a>ICorProfilerInfo3::EnumJITedFunctions メソッド
以前に JIT でコンパイルされたすべての関数の列挙子を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]ポインター、 [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)列挙子。  
  
## <a name="remarks"></a>コメント  
 このメソッドと重なる可能性があります`JITCompilation`など、コールバック、 [icorprofilercallback::jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)メソッドです。 このメソッドによって返された列挙子では、Ngen.exe で生成されたネイティブ イメージから読み込まれた関数は含まれません。  
  
> [!NOTE]
>  返される列挙体には値「0」のみが含まれています、`COR_PRF_FUNCTION::reJitId`フィールドです。  必要な有効な場合`COR_PRF_FUNCTION::reJitId`、値を使用して、 [icorprofilerinfo 4::enumjitedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)メソッドです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
