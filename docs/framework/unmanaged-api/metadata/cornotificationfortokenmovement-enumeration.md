---
title: CorNotificationForTokenMovement 列挙型
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96ab659e6ab6cc9601c0e9a1ab511da92905c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448257"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement 列挙型
トークンの再マップが発生したときに、メタデータ API クライアントに送信される通知を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MDNotifyDefault`|通知のタイミング`mdTypeRef`、 `mdMethodDef`、 `mdMemberRef`、または`mdFieldDef`トークン移動します。|  
|`MDNotifyAll`|任意のトークンを動かしたときに通知します。|  
|`MDNotifyNone`|トークンの移動時に通知しません。|  
|`MDNotifyMethodDef`|通知のタイミング、`mdMethodDef`トークンを移動します。|  
|`MDNotifyMemberRef`|通知のタイミング、`mdMemberRef`トークンを移動します。|  
|`MDNotifyFieldDef`|通知のタイミング、`mdFieldDef`トークンを移動します。|  
|`MDNotifyTypeRef`|通知のタイミング、`mdTypeRef`トークンを移動します。|  
|`MDNotifyTypeDef`|通知のタイミング、`mdTypeDef`トークンを移動します。|  
|`MDNotifyParamDef`|通知のタイミング、`mdParamDef`トークンを移動します。|  
|`MDNotifyInterfaceImpl`|通知のタイミング、`mdInterfaceImpl`トークンを移動します。|  
|`MDNotifyProperty`|通知のタイミング、`mdProperty`トークンを移動します。|  
|`MDNotifyEvent`|通知のタイミング、`mdEvent`トークンを移動します。|  
|`MDNotifySignature`|通知のタイミング、`mdSignature`トークンを移動します。|  
|`MDNotifyTypeSpec`|通知のタイミング、`mdTypeSpec`トークンを移動します。|  
|`MDNotifyCustomAttribute`|通知のタイミング、`mdCustomAttribute`トークンを移動します。|  
|`MDNotifySecurityValue`|通知のタイミング、`mdSecurityValue`トークンを移動します。|  
|`MDNotifyPermission`|通知のタイミング、`mdPermission`トークンを移動します。|  
|`MDNotifyModuleRef`|通知のタイミング、`mdModuleRef`トークンを移動します。|  
|`MDNotifyNameSpace`|通知のタイミング、`mdNameSpace`トークンを移動します。|  
|`MDNotifyAssemblyRef`|通知のタイミング、`mdAssemblyRef`トークンを移動します。|  
|`MDNotifyFile`|通知のタイミング、`mdFile`トークンを移動します。|  
|`MDNotifyExportedType`|通知のタイミング、`mdExportedType`トークンを移動します。|  
|`MDNotifyResource`|通知のタイミング、`mdManifestResource`トークンを移動します。|  
  
## <a name="remarks"></a>コメント  
 トークンが再マップされる (移動) メタデータのマージ中にします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
