---
title: IValidator::Validate メソッド
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf2c343db459879ca95372e104aee68b22dee6b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440618"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate メソッド
指定したポータブル実行可能 (PE) または Microsoft intermediate language (MSIL) ファイルを検証します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `veh`  
 [in]ポインター、`IVEHandler`妥当性確認エラーを処理するインスタンス。  
  
 `pAppDomain`  
 [in]ファイルが読み込まれているアプリケーション ドメインへのポインター。  
  
 `ulFlags`  
 [in]ビットごとの組み合わせ[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)を実行するか、検証を示す値。  
  
 `ulMaxError`  
 [in]検証を終了する前に許可されるエラーの最大数。  
  
 `token`  
 [in]使用しません。  
  
 `fileName`  
 [in]検証に使用するファイルの名前を指定する文字列。  
  
 `pe`  
 [in]ファイルが格納されているメモリ バッファーへのポインター。  
  
 `ulSize`  
 [in]検証に使用するファイルのバイト単位のサイズ。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** IValidator.idl、IValidator.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
