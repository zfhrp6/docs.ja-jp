---
title: IHostMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbf889aaa6a78e67d0f08758adc0bf31cd932e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441349"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc インターフェイス
共通言語ランタイム (CLR) にはホストを介してヒープから詳細な割り当てを要求できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Alloc メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|要求のホストが、ヒープから要求されたメモリ量を割り当てることです。|  
|[DebugAlloc メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|ホストが、ヒープから要求されたメモリ量を割り当てるし、さらに、メモリが割り当てられた場所を追跡を要求します。|  
|[Free メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|使用して割り当てられたメモリを解放、`Alloc`メソッドです。|  
  
## <a name="remarks"></a>コメント  
 CLR へのインターフェイス ポインターの取得、`IHostMalloc`を呼び出してインスタンス、 [ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
