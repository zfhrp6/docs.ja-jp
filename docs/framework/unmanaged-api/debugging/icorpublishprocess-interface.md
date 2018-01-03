---
title: "ICorPublishProcess インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765be4e0ae7657d169ea561bc6a36bcf8cc11153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess インターフェイス
表示するプロセスについての情報にアクセスするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumAppDomains メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|取得、 [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)これによって参照されるプロセス内のアプリケーション ドメインを含むインスタンス`ICorPublishProcess`です。|  
|[GetDisplayName メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|これによって参照されるプロセスの実行可能ファイルの完全なパスを取得`ICorPublishProcess`です。|  
|[GetProcessID メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|これによって参照されるプロセスのオペレーティング システムの識別子を取得`ICorPublishProcess`です。|  
|[IsManaged メソッド](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|これによって、プロセスが参照されるかどうかを示す値を取得`ICorPublishProcess`はマネージ コードを実行する呼ばれます。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorPub.idl、CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish コクラス](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
