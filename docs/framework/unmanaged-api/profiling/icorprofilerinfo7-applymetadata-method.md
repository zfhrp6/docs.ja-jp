---
title: "ICorProfilerInfo7::ApplyMetaData メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e79d687d3d777895dea9427e4865c2fc866f50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7::ApplyMetaData メソッド
[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 新しく定義されたメタデータを適用、`IMetadataEmit::Define*`メソッドを指定されたモジュール。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleID`  
 [in]変更されたメタデータを持つモジュールの識別子。  
  
## <a name="remarks"></a>コメント  
 後のメタデータの変更が加えられた場合、 [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバックを新しいメタデータを使用する前にこのメソッドを呼び出す必要があります。  
  
 `ApplyMetaData`次の種類のメタデータを追加するにのみサポートされています。  
  
-   `AssemblyRef`呼び出して作成した、レコード、 [imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)です。 メソッドをオーバーライドします。  
  
-   `TypeRef`呼び出して作成した、レコード、 [imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)メソッドです。  
  
-   `TypeSpec`呼び出して作成した、レコード、 [imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)メソッドです。  
  
-   `MemberRef`呼び出して作成した、レコード、 [imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)メソッドです。  
  
-   `MemberSpec`呼び出して作成した、レコード、 [imetadataemit 2::definemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)メソッドです。  
  
-   `UserString`呼び出して作成した、レコード、 [imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)メソッドです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
