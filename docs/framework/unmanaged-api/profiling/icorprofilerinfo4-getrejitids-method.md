---
title: "ICorProfilerInfo4::GetReJITIDs メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetReJITIDs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc16cd932fc2ce0cf5cb53c227081501e79ed2d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs メソッド
JIT 再コンパイルのすべてのバージョン指定の関数はまだ割り当てられていることを識別する Id の配列を返します。 これには、後で元に戻されていて (たとえば、元に戻された関数が含まれるアプリケーション ドメインでは、使用されている) ときに解放されていない関数の JIT 再コンパイル バージョンが含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]`FunctionID`関数のインスタンスのバージョンを列挙するのです。  
  
 `cReJitIds`  
 [in]割り当てられた JIT 再コンパイルの Id の数、`reJitIds`配列。  
  
 `pcReJitIds`  
 [out]実際の Id の JIT 再コンパイルの数。  
  
 `reJitIds`  
 [out]指定した関数の JIT 再コンパイルの Id を格納する、呼び出し元が割り当てた配列。  
  
## <a name="remarks"></a>コメント  
 `GetReJITIDs`指定された関数のインスタンスの JIT 再コンパイルのアクティブな Id を列挙します。 その他の同様の使用状況パターンが続く`ICorProfilerInfo`呼び出し元が割り当てたバッファーを受け取る関数をします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
