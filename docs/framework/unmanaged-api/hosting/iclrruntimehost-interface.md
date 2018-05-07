---
title: ICLRRuntimeHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95dd084520d1e93803a91f0c4d01214ed0d3744d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost インターフェイス
類似の機能を提供、 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)バージョン 1 の場合、次の変更と .NET Framework で提供されるインターフェイス。  
  
-   追加、 [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)ホスト コントロールのインターフェイスを設定します。  
  
-   によって提供されるいくつかのメソッドの省略`ICorRuntimeHost`です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ExecuteApplication メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|新しいドメインでアクティブにするアプリケーションを指定するマニフェストに基づく ClickOnce の配置シナリオに使用されます。|  
|[ExecuteInAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|指定します、<xref:System.AppDomain>指定したマネージ コードを実行するためです。|  
|[ExecuteInDefaultAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|指定したアセンブリで指定した型の指定したメソッドを呼び出します。|  
|[GetCLRControl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|型のインターフェイス ポインターを取得[ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)ホストが共通言語ランタイム (CLR) のカスタマイズに使用できます。|  
|[GetCurrentAppDomainId メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|数値識別子を取得、<xref:System.AppDomain>が現在実行されています。|  
|[SetHostControl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|ホスト コントロールのインターフェイスを設定します。 呼び出す必要があります`SetHostControl`呼び出す前に`Start`です。|  
|[Start メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|プロセスに CLR を初期化します。|  
|[Stop メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|ランタイムによってコードの実行を停止します。|  
|[UnloadAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|アンロード、<xref:System.AppDomain>指定した数値識別子に対応します。|  
  
## <a name="remarks"></a>コメント  
 以降で、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]を使用して、 [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)へのポインターを取得するインターフェイス、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイス、およびを呼び出す、 [iclrruntimeinfo::getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)へのポインターを取得するメソッド`ICLRRuntimeHost`です。 .NET Framework の以前のバージョンで、ホストのポインターを取得する、`ICLRRuntimeHost`を呼び出してインスタンス[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)または[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)です。 使用する必要があります、.NET Framework version 2.0 で提供されるテクノロジのいずれかの実装を提供する`ICLRRuntimeHost`の代わりに`ICorRuntimeHost`です。  
  
> [!IMPORTANT]
>  呼び出す必要はありません、[開始](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッドを呼び出す前に、 [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)マニフェスト ベースのアプリケーションをアクティブ化するメソッド。 場合、`Start`メソッドが最初と呼ばれる、`ExecuteApplication`メソッドの呼び出しは失敗します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [CorBindToCurrentRuntime 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeEx 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CLRRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
