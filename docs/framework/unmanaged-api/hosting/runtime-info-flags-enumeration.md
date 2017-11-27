---
title: "RUNTIME_INFO_FLAGS 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 697111efbb4e3f705c881ec677f781b6e3e6959d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS 列挙型
共通言語ランタイム (CLR) に関する情報を返す必要がありますを示す値を含みます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|ディレクトリ情報を含める必要があることを示します。|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|バージョン情報を含める必要があることを示します。|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|エラー発生時にエラー ダイアログ ボックスを表示しないことを示します。|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|示します呼び出しの影響、 [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) SEM_FAILCRITICALERRORS フラグを持つ関数をオーバーライドする必要があります。 抑制されるのではなく、障害発生時にインストール ダイアログ ボックスを表示する必要があります。|  
|`RUNTIME_INFO_REQUEST_AMD64`|AMD 64 互換性のあるバージョンのランタイムに関する情報を要求を示します。|  
|`RUNTIME_INFO_REQUEST_IA64`|IA 64 互換性のあるバージョンのランタイムに関する情報を要求を示します。|  
|`RUNTIME_INFO_REQUEST_X86`|X86 と互換性のあるバージョンのランタイムに関する情報を要求を示します。|  
|`RUNTIME_INFO_UPGRADE_VERSION`|含めることを示すバージョン情報をアップグレードする必要があります。|  
  
## <a name="remarks"></a>コメント  
 次のプラットフォーム アーキテクチャ フラグは、一度に 1 つのみ指定でき、組み合わせることができません。  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスティングの列挙体](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
