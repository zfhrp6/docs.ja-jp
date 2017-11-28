---
title: "INotifyConnection2::UnregisterNotifySource メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.UnregisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 063a146d31031f0cb14e00278819e8cd874f98c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="inotifyconnection2unregisternotifysource-method"></a>INotifyConnection2::UnregisterNotifySource メソッド
接続から、指定された通知のソース オブジェクトを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `in_pNotifySource`  
 [in]登録解除する通知オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>関連項目  
 [INotifyConnection2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [INotifySource2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [INotifySink2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [RegisterNotifySource メソッド](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
