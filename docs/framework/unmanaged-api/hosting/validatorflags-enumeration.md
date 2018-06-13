---
title: ValidatorFlags 列挙型
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20ce52108c1024ad3e07051b226aa65612580e2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441391"
---
# <a name="validatorflags-enumeration"></a>ValidatorFlags 列挙型
呼び出しで実行される検証の種類を示す値を含む、 [iclrvalidator::validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|のみ Microsoft intermediate language (MSIL)、実行可能ファイルを検証することを指定します。|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|実行可能ファイルの形式に関するのみを検証することを指定します。|  
|`VALIDATOR_EXTRA_VERBOSE`|すべての種類の検証を実行ありで報告されることを指定します。|  
|`VALIDATOR_NOCHECK_PEFORMAT`|実行可能ファイルの形式を検証しないことを指定します。|  
|`VALIDATOR_SHOW_SOURCE_LINES`|検証エラー メッセージが検証エラーが発生するソース コードの行を含める必要がありますを指定します。 .NET Framework version 2.0 でこのフィールドの値が正しくありません。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** IValidator.idl、IValidator.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRErrorReportingManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
