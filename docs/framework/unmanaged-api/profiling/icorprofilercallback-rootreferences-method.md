---
title: ICorProfilerCallback::RootReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 467d065ab4d47e698c7043697ebe2ccf5f98a3cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452586"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences メソッド
ガベージ コレクション後のルート参照に関する情報をプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cRootRefs`  
 [in]参照の数、`rootRefIds`配列。  
  
 `rootRefIds`  
 [in]静的オブジェクトまたはスタック上のオブジェクトのいずれかを参照するオブジェクト Id の配列。  
  
## <a name="remarks"></a>コメント  
 両方`RootReferences`と[icorprofilercallback 2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)をプロファイラーに通知と呼ばれます。 プロファイラーは、どちらか一方、実装通常しますが、どちらの情報が渡されるため`RootReferences2`に渡されたのスーパー セット`RootReferences`です。  
  
 可能であれば、 `rootRefIds` null オブジェクトを格納する配列。 たとえば、スタックで宣言されているすべてのオブジェクト参照は、ガベージ コレクターによってルートとして扱われは常に報告されます。  
  
 によって返されるオブジェクト Id`RootReferences`自体には、コールバック中に無効なため古いアドレスから新しいアドレスにオブジェクトを移動中にガベージ コレクションがある可能性があります。 そのため、プロファイラーは、中にオブジェクトを検査する試みる必要がありますいないを`RootReferences`呼び出します。 ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、すべてのオブジェクトの新しい場所に移動されましたし、安全に検査することができます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
