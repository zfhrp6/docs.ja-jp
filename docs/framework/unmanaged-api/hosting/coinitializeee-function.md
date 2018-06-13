---
title: CoInitializeEE 関数
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bbd25909e70826f8cd29076c1eb62a4da6779cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435402"
---
# <a name="coinitializeee-function"></a>CoInitializeEE 関数
共通言語ランタイムの実行エンジンがプロセスに読み込まれることになります。 この関数は非推奨、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。 使用して、 [iclrruntimehost::start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fFlags`  
 [in]1 つ、 [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)列挙定数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、Winerror.h、および次の表の値で定義されている標準の COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|実行エンジンは正常に読み込まれます。|  
|S_FALSE|実行エンジンは既に読み込まれています。|  
|E_FAIL|実行エンジンを読み込むことができませんでした。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、既に読み込まれていない場合に、実行エンジンを読み込みます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
