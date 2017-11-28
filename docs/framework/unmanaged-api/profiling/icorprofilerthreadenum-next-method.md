---
title: "ICorProfilerThreadEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Next
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3295f3dc9af50fb62a2008f59819a51a6032a48b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumnext-method"></a>ICorProfilerThreadEnum::Next メソッド
スレッドのシーケンシャル コレクションから、列挙子の現在の位置以降にある指定した数の隣接するスレッドを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in] 取得するスレッドの数。  
  
 `ids`  
 [out] `ThreadID` 値の配列。それぞれの値は、取得されたスレッドを表します。  
  
 `pceltFetched`  
 [out] `ids` 配列で実際に返されるスレッドの数へのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`celt` 要素が返されました。|  
|S_FALSE|`celt` よりも少ない数の要素が返されました。これは、列挙が完了したことを示します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerThreadEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
