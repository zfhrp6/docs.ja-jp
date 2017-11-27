---
title: "IHostAssemblyStore インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore インターフェイス
アセンブリおよび共通言語ランタイム (CLR) とは無関係にモジュールの読み込みにホストできるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ProvideAssembly メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|によって参照されているアセンブリへの参照を取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)への呼び出しから返された[ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)です。|  
|[ProvideModule メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|アセンブリまたはリンク (組み込まれていない) のリソース ファイル内のモジュールを解決します。|  
  
## <a name="remarks"></a>コメント  
 `IHostAssemblyStore`アセンブリ id に基づく効率的にアセンブリを読み込むホスト方法を提供します。 ホストを返すことによってアセンブリを読み込んで`IStream`バイトを直接ポイントするインスタンス。  
  
 CLR では、ホストが実装されているかどうかを判断`IHostAssemblyStore`を呼び出して`IHostAssemblyManager::GetNonHostAssemblyStores`初期化時にします。 これにより、ホスト、たとえば、.NET Framework アセンブリへのバインドをランタイムに依存するが、ユーザー アセンブリへのバインドを制御します。  
  
> [!NOTE]
>  実装を提供する`IHostAssemblyStore`、ホストによって参照されていないすべてのアセンブリを解決するのにはその目的を指定する、`ICLRAssemblyReferenceList`から返された`IHostAssemblyManager::GetNonHostStoreAssemblies`です。  
  
> [!NOTE]
>  によって提供されるように、.NET Framework version 2.0 が、アセンブリのネイティブ イメージの読み込みにホストの方法を提供しません、[ネイティブ イメージ ジェネレーター (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)ユーティリティです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
