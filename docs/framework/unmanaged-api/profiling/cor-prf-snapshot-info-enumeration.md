---
title: "COR_PRF_SNAPSHOT_INFO 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SNAPSHOT_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SNAPSHOT_INFO
helpviewer_keywords: COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a9c854360881426f2fc7fc9e401da1dc93b9bd84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corprfsnapshotinfo-enumeration"></a>COR_PRF_SNAPSHOT_INFO 列挙型
プロファイラーの各呼び出しにスタック スナップショットを使用して渡すデータをバックアップする作業がどの程度を示す[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)関数。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|すべての値を渡す必要があることを示します`StackSnapshotCallback`パラメーターを除く、`context`パラメーター。|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|すべての値を渡す必要があることを示します`StackSnapshotCallback`などのパラメーター、`context`パラメーター。|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|単純化し、別のスタック ウォーク アルゴリズムを使用することを示します。|  
  
## <a name="remarks"></a>コメント  
 によって指定された値を`COR_PRF_SNAPSHOT_INFO`へのパラメーターとして渡される列挙型、 [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [DoStackSnapshot メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [列挙体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
