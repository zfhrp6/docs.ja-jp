---
title: NukeDownloadedCache 関数
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0436991512713c05e60a3c10d6fbdaa17bb378c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429828"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache 関数
共通言語ランタイム (CLR) のダウンロード キャッシュを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、WinError.h で定義されている標準の COM エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 CLR ダウンロード キャッシュは、再利用できる場合、URL からダウンロードされている厳密な名前のアセンブリが格納領域です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** Fusion.dll と Mscorwks.dll です。 Mscorwks.dll の代わりに Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認してください。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [CreateHistoryReader 関数](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [GetHistoryFileDirectory 関数](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
