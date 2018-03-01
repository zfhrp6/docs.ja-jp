---
title: "IMethodMalloc インターフェイス"
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
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1941a46a60219d9dd56d162f89baf268f220c102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc インターフェイス
新しい Microsoft intermediate language (MSIL) 関数本体にメモリを割り当てる方法を提供します。  
  
> [!NOTE]
>  `IMethodMalloc`インターフェイスは、単純なメモリ アロケーター。 これにより、メモリを割り当てるには、解放することができます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Alloc メソッド](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|新しい MSIL 関数本体の指定した量のメモリを割り当てようとします。|  
  
## <a name="remarks"></a>コメント  
 各アロケーターはモジュール固有であり、関数本体がモジュールのベースから正の値のオフセット位置にあることを確認します。 モジュールのベースを超えるメモリ アロケーターを使用すると、関数本体にのみメモリを割り当てるため、貴重なことはできます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
