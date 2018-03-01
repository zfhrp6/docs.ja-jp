---
title: "ICorProfilerObjectEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e5c44c819f8a92b48c66dcc4c03a576bb9b5bd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum インターフェイス
によって生成される固定されたオブジェクトのコレクションを順番に反復処理するメソッドを提供、 [Ngen.exe (ネイティブ イメージ ジェネレーター)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|この `ICorProfilerObjectEnum` インターフェイスのコピーに対するインターフェイス ポインターを取得します。|  
|[GetCount メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|コレクション内で固定されたオブジェクトの合計数を取得します。|  
|[Next メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|列挙子の現在の位置からのオブジェクトのシーケンシャル コレクションから指定された数の隣接するオブジェクトを取得します。|  
|[Reset メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|この列挙子のカーソルをシーケンスの開始位置に移動します。|  
|[Skip メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|指定した要素数がスキップされるように、現在の位置からこの列挙子のカーソルを進めます。|  
  
## <a name="remarks"></a>コメント  
 `ICorProfilerObjectEnum` インターフェイスは列挙子です。 このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。 言い換えると、受信側は配列要素のフローを明示的に制御できる大きな配列をメソッドのパラメーターとして渡すことに関連する問題を回避します。  
  
 使用して[icorprofilerinfo 2::enummodulefrozenobjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)へのポインターを取得する、`ICorProfilerObjectEnum`インターフェイスです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumModuleFrozenObjects メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
