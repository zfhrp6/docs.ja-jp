---
title: IHostMemoryManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3edae4cb112f46643734c5f1612d9df36ad47e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441333"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager インターフェイス
標準の Win32 仮想メモリ関数を使用する代わりに、共通言語ランタイム (CLR) はホストを介して仮想メモリの要求を行うことができるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|共通言語ランタイム (CLR) が、オペレーティング システムから指定されたメモリを取得したことをホストに通知します。|  
|[CreateMAlloc メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|インターフェイス ポインターを取得、 [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)ホストによって作成されたヒープからメモリの割り当てを要求するために使用するインスタンス。|  
|[GetMemoryLoad メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|ホストで報告された、現在使用されている物理メモリの量を取得します。|  
|[NeedsVirtualAddressSpace メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|CLR が指定されたメモリを使用しようとしています。 しようとしていることをホストに通知します。|  
|[RegisterMemoryNotificationCallback メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|ホストが、現在のメモリ負荷、コンピューター上の CLR に通知するために呼び出すコールバック関数へのポインターを登録します。|  
|[ReleasedVirtualAddressSpace メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|指定されたメモリを使用して、CLR が完了したことをホストに通知します。|  
|[VirtualAlloc メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|対応する Win32 関数では、予約または呼び出し元のプロセス仮想アドレス空間内のページの領域をコミットの論理ラッパーとして機能します。|  
|[VirtualFree メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|解放、デコミット、または解放され、呼び出し元のプロセス仮想アドレス空間内のページの領域をデコミット、対応する Win32 関数の論理ラッパーとして機能します。|  
|[VirtualProtect メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|対応する Win32 関数では、呼び出し元プロセスの仮想アドレス空間でコミットされたページの領域に保護を変更する論理ラッパーとして機能します。|  
|[VirtualQuery メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|対応する Win32 関数では、呼び出し元プロセスの仮想アドレス空間内のページの範囲に関する情報を取得する論理ラッパーとして機能します。|  
  
## <a name="remarks"></a>コメント  
 `IHostMemoryManager` また、CLR ホストによって報告された、ヒープのメモリ要求を行うと、プロセスでは、メモリ不足のレベルを取得するためのポインターを取得するためのメソッドを提供します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IHostMalloc インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
