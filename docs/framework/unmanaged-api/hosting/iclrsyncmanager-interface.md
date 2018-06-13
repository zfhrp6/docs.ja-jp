---
title: ICLRSyncManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b87ccc3d6c3e957d0384499048032e35247093a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436482"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager インターフェイス
要求されたタスクに関する情報を取得し、同期実装でデッドロックを検出するためにホストできるようにするメソッドを定義します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator メソッド](iclrsyncmanager-createrwlockowneriterator-method.md)|共通言語ランタイム (CLR) を使用して、一連のリーダー ライター ロックを待機してタスクを決定するホストの反復子を作成するように要求します。|  
|[DeleteRWLockOwnerIterator メソッド](iclrsyncmanager-deleterwlockowneriterator-method.md)|CLR がへの呼び出しによって作成された反復子を破棄することを要求`CreateRWLockOwnerIterator`です。|  
|[GetMonitorOwner メソッド](iclrsyncmanager-getmonitorowner-method.md)|指定したモニターを所有するタスクを取得します。|  
|[GetRWLockOwnerNext メソッド](iclrsyncmanager-getrwlockownernext-method.md)|現在のリーダー ライター ロックを待機している次のタスクを取得します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread>  
 [IHostSyncManager インターフェイス](ihostsyncmanager-interface.md)  
 [マネージ コードとアンマネージ スレッド処理](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [ホスト インターフェイス](hosting-interfaces.md)
