---
title: "ICorRuntimeHost インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost
helpviewer_keywords: ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b115b8d52f904fef41a2e85c1192a18e5c3d3e08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost インターフェイス
ホストが起動し、作成して既定のドメインにアクセスして、プロセスで実行されているすべてのドメインを列挙するアプリケーション ドメインを構成する共通言語ランタイム (CLR) を明示的に停止できるようにするメソッドを提供します。  
  
 .NET framework version 2.0 では、このインターフェイスはによって置き換え[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CloseEnum メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|ドメイン リストの先頭に戻るには、ドメインの列挙子をリセットします。|  
|[CreateDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|アプリケーション ドメインを作成します。 呼び出し元は、型のインターフェイス ポインターを受け取ります<xref:System._AppDomain>型のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>です。|  
|[CreateDomainEx メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|アプリケーション ドメインを作成します。 この方法では、呼び出し、返されたその他の機能を構成する IAppDomainSetup インスタンス<xref:System._AppDomain>インスタンス。|  
|[CreateDomainSetup メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|型のインターフェイス ポインターを取得`IAppDomainSetup`を<xref:System.AppDomainSetup>インスタンス。 `IAppDomainSetup`作成する前に、アプリケーション ドメインの側面を構成する方法を提供します。|  
|[CreateEvidence メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|型のインターフェイス ポインターを取得<xref:System.Security.Principal.IIdentity>、これにより、ホストに渡すセキュリティ証拠を作成する[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)または[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)です。|  
|[CreateLogicalThreadState メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|使用しないでください。|  
|[CurrentDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|型のインターフェイス ポインターを取得<xref:System._AppDomain>を表す現在のスレッドで読み込まれているドメインです。|  
|[DeleteLogicalThreadState メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|使用しないでください。|  
|[EnumDomains メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|現在のプロセスで、ドメインの列挙子を取得します。|  
|[GetConfiguration メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|ホストが CLR のコールバックの構成を指定できるようにするオブジェクトを取得します。|  
|[GetDefaultDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|型のインターフェイス ポインターを取得<xref:System._AppDomain>現在のプロセスの既定のドメインを表すです。|  
|[LocksHeldByLogicalThread メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|使用しないでください。|  
|[MapFile メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|メモリに指定されたファイルをマップします。 このメソッドは、互換性のために残されています。|  
|[NextDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|列挙体の次のドメインへのインターフェイス ポインターを取得します。|  
|[Start メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|CLR を起動します。|  
|[Stop メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|現在のプロセスのランタイムでコードの実行を停止します。|  
|[SwitchInLogicalThreadState メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|使用しないでください。|  
|[SwitchOutLogicalThreadState メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|使用しないでください。|  
|[UnloadDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|現在のプロセスから指定されたアプリケーション ドメインをアンロードします。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** 1.0、1.1  
  
## <a name="see-also"></a>参照  
 <xref:System.AppDomain>  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [ランタイム ホスト](http://msdn.microsoft.com/en-us/99d9246a-b994-4fe5-985c-8588d1d59998)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
