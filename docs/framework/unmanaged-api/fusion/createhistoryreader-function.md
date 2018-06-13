---
title: CreateHistoryReader 関数
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3a3cc21dbbcfa99ddcecb534bd2e337da005597
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431179"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader 関数
指定したファイルの履歴のリーダーを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wzFilePath`  
 [in]ファイルのパス。  
  
 `ppHistoryReader`  
 [out]正常に完了すると、履歴リーダーへのポインターを格納します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の表で説明する値に加えて、WinError.h で定義されている標準の COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドが正常に完了したことを示します。|  
|E_INVALIDARG|示します`wzFilePath`または`ppHistoryReader`の参照を null に設定されます。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ライブラリ:** Fusion.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
