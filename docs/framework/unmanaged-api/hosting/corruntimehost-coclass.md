---
title: "CorRuntimeHost コクラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRuntimeHost
helpviewer_keywords: CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23bee1a79dfb54a696495fdb61a7ba9ba4b4c143
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost コクラス
共通言語ランタイムで実行されているアプリケーションを管理するためのインターフェイスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>インターフェイス  
  
|Interface|説明|  
|---------------|-----------------|  
|[ICorConfiguration インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|共通言語ランタイム (CLR) を構成するためのメソッドを提供します。|  
|[ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|ホストが起動し、作成して既定のドメインにアクセスして、プロセスで実行されているすべてのドメインを列挙するアプリケーション ドメインを構成する共通言語ランタイムを明示的に停止できるようにするメソッドを提供します。|  
|[IDebuggerInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|デバッグ サービスの状態に関する情報を取得するためのメソッドを提供します。|  
|[IGCHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。|  
|"IValidator"|ポータブル実行可能イメージの検証と検証エラーの詳細なレポート作成のメソッドを提供します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ホスト コクラス](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
