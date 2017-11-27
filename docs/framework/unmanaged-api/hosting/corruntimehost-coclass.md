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
ms.openlocfilehash: 3d7a272aff3a3c7d32042b76d37fdb15c9dcad4d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
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
  
|インターフェイス|説明|  
|---------------|-----------------|  
|[ICorConfiguration インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|共通言語ランタイム (CLR) を構成するためのメソッドを提供します。|  
|[ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|ホストが起動し、作成して既定のドメインにアクセスして、プロセスで実行されているすべてのドメインを列挙するアプリケーション ドメインを構成する共通言語ランタイムを明示的に停止できるようにするメソッドを提供します。|  
|[IDebuggerInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|デバッグ サービスの状態に関する情報を取得するためのメソッドを提供します。|  
|[IGCHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。|  
|"IValidator"|ポータブル実行可能イメージの検証と検証エラーの詳細なレポート作成のメソッドを提供します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト コクラス](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
