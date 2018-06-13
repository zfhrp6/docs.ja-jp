---
title: ICorProfilerCallback2::RootReferences2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abf92749e1139a85ea2f49fb5d5caff69ce39c24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458462"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 メソッド
ガベージ コレクションが発生した後は、ルート参照について、プロファイラーを通知します。 このメソッドは、の拡張機能、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cRootRefs`  
 [in]内の要素の数、 `rootRefIds`、 `rootKinds`、 `rootFlags`、および`rootIds`配列。  
  
 `rootRefIds`  
 [in]オブジェクト Id は、静的オブジェクトまたはスタック上のオブジェクトのいずれかの参照の配列。 内の要素、`rootKinds`配列に対応する要素を分類する情報を提供する、`rootRefIds`配列。  
  
 `rootKinds`  
 [in]配列[COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)ガーベッジ コレクション ルートの種類を示す値。  
  
 `rootFlags`  
 [in]配列[COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)ガーベッジ コレクション ルートのプロパティを記述する値。  
  
 `rootIds`  
 [in]値に応じて、ガーベッジ コレクション ルートについての追加情報を含む整数を指す値 UINT_PTR の配列、`rootKinds`パラメーター。  
  
 ルートの種類が、スタックの場合は、ルート ID は、変数を含む関数です。 ルート ID が 0 の場合、関数、clr の内部にある名前のない機能です。 ルートの種類が、ハンドルである場合は、ルート ID は、ガベージ コレクション ハンドルのです。 その他のルート型の ID 非透過の値は、無視してください。  
  
## <a name="remarks"></a>コメント  
 `rootRefIds`、 `rootKinds`、 `rootFlags`、および`rootIds`配列は並列配列です。 つまり、 `rootRefIds[i]`、 `rootKinds[i]`、 `rootFlags[i]`、および`rootIds[i]`すべての対象ルートは同じです。  
  
 両方`RootReferences`と`RootReferences2`をプロファイラーに通知と呼ばれます。 プロファイラーは通常 1 つのメソッドや、他の両方ではなく、ために実装に渡された情報`RootReferences2`に渡されたのスーパー セット`RootReferences`です。  
  
 内のエントリ可能であれば`rootRefIds`を対応するルート参照が null と、マネージ ヒープ上のオブジェクトを参照していないことを意味する 0 にします。  
  
 によって返されるオブジェクト Id`RootReferences2`自体には、コールバック中に無効なため古いアドレスから新しいアドレスにオブジェクトを移動中にガベージ コレクションがある可能性があります。 このため、`RootReferences2` 呼び出しの間、プロファイラーはオブジェクトを検査するべきではありません。 ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、すべてのオブジェクトの新しい場所に移動されましたし、安全に検査することができます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
