---
title: ICLRAppDomainResourceMonitor インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc2326c72c9a1c63c4740608e120ace5dc83ebee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434871"
---
# <a name="iclrappdomainresourcemonitor-interface"></a>ICLRAppDomainResourceMonitor インターフェイス
アプリケーション ドメインのメモリおよび CPU 使用率を検査するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCurrentAllocated メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|(バイト単位) の作成後、ガベージ コレクションが行われたメモリ差し引かれません、アプリケーション ドメインによって行われたすべてのメモリ割り当ての合計サイズを取得します。|  
|[GetCurrentSurvived メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|最後のフル ブロッキング ガベージ コレクションで残ったをして、現在のアプリケーション ドメインによって参照されているバイト数を取得します。|  
|[GetCurrentCpuTime メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|アプリケーション ドメインが作成されたため、現在のアプリケーション ドメインで実行中にすべてのスレッドによって使用されている合計プロセッサ時間を取得します。|  
  
## <a name="remarks"></a>コメント  
 `ICLRAppDomainResourceMonitor`インターフェイスには、次のマネージ プロパティを次のような機能が用意されています。  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [\<appDomainResourceMonitoring > 要素](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [アプリケーション ドメインのリソース監視](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
