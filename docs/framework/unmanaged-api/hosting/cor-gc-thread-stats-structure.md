---
title: "COR_GC_THREAD_STATS 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_THREAD_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_THREAD_STATS
helpviewer_keywords: COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10366d183ed7fd7386609e4c5726df0cea4e29a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corgcthreadstats-structure"></a>COR_GC_THREAD_STATS 構造体
ガベージ コレクションに関連するスレッドごとの統計情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`PerThreadAllocation`|現在関連付けられているスレッドに割り当てられたメモリのバイト数`COR_GC_THREAD_STATS`インスタンス。 この番号は、ジェネレーション 0 ガベージ コレクションが発生するたびに 0 にクリアされます。|  
|`Flags`|バイト数では、最新のガベージ コレクションを上位のジェネレーションに昇格します。|  
  
## <a name="remarks"></a>コメント  
 [Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)型の出力パラメーターを取る`COR_GC_THREAD_STATS`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** GCHost.idl  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
