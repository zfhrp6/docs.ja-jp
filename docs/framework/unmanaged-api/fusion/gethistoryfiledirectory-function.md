---
title: "GetHistoryFileDirectory 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHistoryFileDirectory
api_location: fusion.dll
api_type: DLLExport
f1_keywords: GetHistoryFileDirectory
helpviewer_keywords: GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d0ec18a4f95d0d280a66b3b9d9200c560f5f187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory 関数
アプリケーション履歴ディレクトリのパスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wzDir`  
 [out]アプリケーション履歴ディレクトリへのパスを保持するバッファー。  
  
 `pdwSize`  
 [入力、出力].バッファーの長さ。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値だけでなく WinError.h ファイルで定義されている標準の COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`wzDir`または`pdwSize`が null の場合、またはバージョン文字列が正しくありません。|  
  
## <a name="remarks"></a>コメント  
 正常完了時に、`pdwSize`引数が、パス文字列の長さに設定します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** Fusion.dll と Mscorwks.dll です。 Mscorwks.dll の代わりに Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認してください。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [CreateHistoryReader 関数](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [NukeDownloadedCache 関数](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
