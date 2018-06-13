---
title: CorpubPublish コクラス
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9941a9be7d9f68255636b405db29a623be8d37e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406439"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish コクラス
アプリケーション ドメインとプロセスに関する情報を発行するためのインターフェイスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>インターフェイス  
  
|Interface|説明|  
|---------------|-----------------|  
|[ICorPublish インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|これらのプロセスのプロセスとのアプリケーション ドメインに関する情報を公開するためのメソッドを提供します。|  
|[ICorPublishAppDomain インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|表していると、プロセス内のアプリケーション ドメインに関する情報を提供します。|  
|[ICorPublishAppDomainEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|現在プロセス内に存在するアプリケーション ドメインのコレクションを走査するメソッドを提供します。|  
|[ICorPublishProcess インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|コンピューターで実行されているプロセスを表します。|  
|[ICorPublishProcessEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|コンピューターで実行されているプロセスのコレクションを走査するメソッドを提供します。|  
  
## <a name="remarks"></a>コメント  
 一般的な発行シナリオには、開発者がアプリケーション ドメイン内のコンピューターで実行されているマネージ コードをデバッグする場合が含まれます。 ホスティング環境では、プロセス内で 1 つ以上のアプリケーション ドメインが実行されている可能性があります。 すべてのコンピューターで実行されているプロセスを一覧表示するグラフィカル ユーザー インターフェイスまたはその他の手段を使用して、特定のプロセスを選択して、開発者と思います。 一覧には、すべてのマネージ コードを実行しているプロセス内でアプリケーション ドメインを含める必要があります。 開発者は、特定のアプリケーション ドメインを識別し、そのドメインにデバッガーをアタッチします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorPub.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
