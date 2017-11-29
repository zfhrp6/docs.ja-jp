---
title: "IGCHost インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost
helpviewer_keywords: IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0f398c09569a855291a1565ce63b513161a803
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="igchost-interface"></a>IGCHost インターフェイス
ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。  
  
> [!NOTE]
>  以降で、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、使用することができます、 [igchost 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズの値より大きいに設定する方法、`DWORD`によって課される制限、 [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)メソッドです。  
  
> [!NOTE]
>  インターフェイスは上級者のみです。 不適切に使用する場合に、アプリケーションのパフォーマンスに影響ことができます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Collect メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|現在のガベージ コレクションの状態に関係なく、特定のジェネレーションで発生するコレクションを強制的にします。|  
|[GetStats メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|ガベージ コレクション システムの現在の状態の統計情報を取得します。|  
|[GetThreadStats メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|ガベージ コレクションのスレッドあたりの統計情報を取得します。|  
|[SetGCStartupLimits メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|ジェネレーション 0 のセグメントのサイズと最大サイズを設定します。|  
|[SetVirtualMemLimit メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|ランタイムの仮想メモリの最大サイズを設定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** GCHost.idl、GCHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
