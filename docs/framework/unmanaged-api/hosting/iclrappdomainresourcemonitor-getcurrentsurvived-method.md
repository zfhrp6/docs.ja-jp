---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived メソッド
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c179ba23be07e8ff77e1397ed753d4287b22440
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived メソッド
最後のフル ブロッキング ガベージ コレクションで残ったをして、現在のアプリケーション ドメインによって参照されているバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwAppDomainId`  
 [in]要求されたアプリケーション ドメインの ID。  
  
 `pAppDomainBytesSurvived`  
 [out]このアプリケーション ドメインによって保持されている最後のガベージ コレクションの後に残ったバイト数へのポインター。 完全なコレクションの後にこの番号は正確で完全です。 短期コレクションの後に、この番号は完全な可能性のあるではありません。 このパラメーターは、`null` に設定できます。  
  
 `pRuntimeBytesSurvived`  
 [out]最後のガベージ コレクションの後に残ったバイトの総数へのポインター。 完全なコレクションの後に、この数は、マネージ ヒープ内に保持されているバイト数を表します。 短期コレクションの後は、この数は短期のジェネレーションにライブで保持されているバイト数を表します。 このパラメーターは、`null` に設定できます。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|COR_E_APPDOMAINUNLOADED|アプリケーション ドメインがアンロードされたか、存在しません。|  
  
## <a name="remarks"></a>コメント  
 統計がフル ブロッキング ガベージ コレクション後にのみ更新されます。つまり、すべてのジェネレーションが含まれていると、コレクションの中に、アプリケーションが停止するコレクションが発生します。 たとえば、<xref:System.GC.Collect?displayProperty=nameWithType>メソッドのオーバー ロードがフル ブロッキング コレクションを実行します。 同時実行ガベージ コレクションは、バック グラウンドで行われ、アプリケーションをブロックしません。  
  
 `GetCurrentSurvived`メソッドは、アンマネージ相当するマネージ<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>プロパティです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRAppDomainResourceMonitor インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [アプリケーション ドメインのリソース監視](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
