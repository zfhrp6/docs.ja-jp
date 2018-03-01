---
title: "IMethodMalloc::Alloc メソッド"
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
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26998e8b2e8648b4fb175f188540e7bc33c580c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc メソッド
新しい Microsoft intermediate language (MSIL) 関数本体の指定した量のメモリを割り当てようとします。  
  
## <a name="syntax"></a>構文  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cb`  
 [in]メソッドの本体を割り当てることのバイト数。  
  
## <a name="remarks"></a>コメント  
 割り当てられたメモリは、このアロケーターに関連付けられているモジュールのベース アドレスより大きいアドレスから開始されます。 つまり、各アロケーターは、特定のモジュールが作成されはそのベース アドレスから正のオフセットにメモリを割り当てようとします。 場合`Alloc`要求されたモジュールのベース アドレスより大きいアドレスにあるバイト数の割り当てが失敗した実際のメモリ領域の使用可能な量に関係なく、E_OUTOFMEMORY を返します。  
  
 `Alloc`メソッドを組み合わせて使用する必要があります、 [icorprofilerinfo::setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)メソッドです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** WindSee[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IMethodMalloc インターフェイス](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
