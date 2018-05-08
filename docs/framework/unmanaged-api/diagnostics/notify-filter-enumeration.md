---
title: NOTIFY_FILTER 列挙体
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98c3e1ed3da209cbded5d76d938d2420fce606be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="notifyfilter-enumeration"></a>NOTIFY_FILTER 列挙体
デバッガーの関数のコールバックを識別します。 詳細については、次を参照してください。、 [inotifysource 2::setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|示します、 [inotifysink 2::onsynccallout](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)メソッドを呼び出す必要があります。|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|示します、 [inotifysink 2::onsynccallenter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)メソッドを呼び出す必要があります。|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|示します、 [inotifysink 2::onsynccallexit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)メソッドを呼び出す必要があります。|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|示します、 [inotifysink 2::onsynccallreturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)メソッドを呼び出す必要があります。|  
|`NOTIFY_FILTER_ALLSYNC`|示すすべての[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)メソッドを呼び出す必要があります。|  
|`NOTIFY_FILTER_ALL`|既存および将来のすべての通知をアクティブにします。|  
|`NOTIFY_FILTER_NONE`|通知メソッドを呼び出す必要がないことを示します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>関連項目  
 [シンボル ストア診断列挙型](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
