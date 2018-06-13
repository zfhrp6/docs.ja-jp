---
title: ICLRGCManager2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb6cff796a6a7b866357d51350b7b026b019745e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436294"
---
# <a name="iclrgcmanager2-interface"></a>ICLRGCManager2 インターフェイス
ホストが共通言語ランタイムのガベージ コレクション システムとやり取りできるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[SetGCStartupLimitsEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズを設定します。 により、ジェネレーション 0 とセグメントのサイズよりも大きい`DWORD`です。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスから継承、 [ICLRGCManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)です。  
  
 共通言語ランタイム (CLR) が、管理されていると、ガベージ コレクションのメカニズムを実装する<xref:System.GC>型です。 ガベージ コレクション システムに関する詳細については、次を参照してください。[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [自動メモリ管理](../../../../docs/standard/automatic-memory-management.md)  
 [COR_GC_STATS 構造体](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
