---
title: "ICorProfilerCallback::AppDomainShutdownFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e681c64017e99eaaf0b786e48ca96b4435b08890
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>ICorProfilerCallback::AppDomainShutdownFinished メソッド
アプリケーション ドメインが、プロセスからアンロードされたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `appDomainId`  
 [in]アプリケーションのアセンブリが格納されているドメインを識別します。  
  
 `hrStatus`  
 [in]かどうか、アプリケーション ドメインがアンロードされました正常を示す HRESULT。  
  
## <a name="remarks"></a>コメント  
 値`appDomainId`後情報の要求に対して無効です、 [icorprofilercallback::appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)メソッドを返します。  
  
 アプリケーション ドメインをアンロードの一部が後に続ける可能性があります、`AppDomainCreationFinished`コールバック。 失敗を示す HRESULT で`hrStatus`は失敗を示します。 ただし、成功 HRESULT で`hrStatus`のみのアプリケーション ドメインをアンロードの最初の部分が成功したことを示します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
