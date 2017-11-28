---
title: "GetDemultiplexedStub 関数 (アンマネージ API リファレンス)"
description: "GetDemultiplexedStub 関数では、Windows の管理から非同期呼び出しの受信をクライアントを支援するためには、オブジェクト転送シンクを作成します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetDemultiplexedStub
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetDemultiplexedStub
helpviewer_keywords: GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a81101acbf65546ea068e6b5a0e8d9045aaadc71
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub 関数
Windows の管理から非同期呼び出しの受信をクライアントを支援するためには、オブジェクト転送シンクを作成します。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>パラメーター

`pObject`  
[in]クライアントのインプロセス実装へのポインター [IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx)です。

`isLocal`  
[in]イベントがローカルかどうかを示すフラグ (`true`)、それ以外の`false`します。

`ppObject`  
[out]クライアントを Windows の管理から非同期呼び出しの受信を支援するためにオブジェクトの転送シンクです。

## <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は`S_OK`(0) です。

関数が失敗した場合、戻り値がゼロ以外のエラー コードです。 拡張エラー情報を取得する呼び出し、 [GetErrorInfo](geterrorinfo.md)関数。
    
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
