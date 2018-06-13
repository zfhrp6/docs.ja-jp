---
title: ICorConfiguration インターフェイス
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63699f0af69b3a7623c5e9da156c2ff8ae83ccfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437525"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration インターフェイス
共通言語ランタイム (CLR) を構成するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AddDebuggerSpecialThread メソッド](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|デバッグ サービスを特定のスレッドがデバッガーがマネージまたはアンマネージ デバッグ シナリオの中に停止したアプリケーションの実行を続行できることを示します。|  
|[SetDebuggerThreadControl メソッド](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|デバッグ サービスは CLR スレッドをブロックまたはブロック解除されたデバッグときに呼び出すコールバック インターフェイスを設定します。|  
|[SetGCHostControl メソッド](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|仮想メモリの制限を変更するホストに要求、ガベージ コレクターが使用するコールバック インターフェイスを設定します。|  
|[SetGCThreadControl メソッド](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|それ以外の場合のみがブロックされるガベージ コレクションの非ランタイム タスクのスレッドのスケジュールのコールバック インターフェイスを設定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
